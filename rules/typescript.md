# TypeScript Strict & Anti-Cheat Rules

Tài liệu này định nghĩa các quy chuẩn TypeScript bắt buộc cho dự án. Mọi mã nguồn TypeScript/TSX trong dự án phải tuân thủ nghiêm ngặt các quy tắc dưới đây.

---

## 1. Nguyên Tắc Cốt Lõi: Anti-Cheat & Strict Typing

### A. Tuyệt Đối Không Dùng `any`
- **CẤM** sử dụng kiểu `any` trong toàn bộ mã nguồn ứng dụng (kể cả test hay helper).
- Sử dụng `unknown` khi nhận dữ liệu từ bên ngoài (API, User Input, Third-party SDK, LocalStorage).
- Ép buộc phải **thu hẹp kiểu (Type Narrowing)** trước khi truy cập thuộc tính của `unknown`.

```typescript
// SAI: Dùng any làm mất type-safety
function handleApiResponse(response: any) {
  console.log(response.data.user.name);
}

// ĐÚNG: Dùng unknown và thu hẹp kiểu an toàn
interface UserData {
  user: { name: string };
}

function isUserData(data: unknown): data is UserData {
  return (
    typeof data === 'object' &&
    data !== null &&
    'user' in data &&
    typeof (data as Record<string, unknown>).user === 'object'
  );
}

function handleApiResponse(response: unknown) {
  if (isUserData(response)) {
    console.log(response.user.name);
  }
}
```

### B. Cấm Ép Kiểu Mù Quáng (`Type Assertion Cheating`)
- **CẤM** dùng cú pháp `as unknown as T` hoặc `as any` để "lừa" compiler nhằm dập tắt lỗi biên dịch.
- **CẤM** sử dụng comment vô hiệu hóa type check: `// @ts-ignore` hoặc `// @ts-nocheck`.
- Nếu gặp lỗi type không khớp, phải điều chỉnh type definition hoặc xử lý data runtime đúng kiểu.
- Chỉ dùng `as const` hoặc assertion đơn lẻ khi có cơ chế bảo vệ (`type guard`) rõ ràng.

---

## 2. Types & Interfaces

### A. Public APIs & Exported Functions
- Mọi hàm được `export` (hàm tiện ích, hook, API caller, service) bắt buộc phải khai báo rõ ràng kiểu tham số (`parameters`) và kiểu trả về (`return type`).
- Biến cục bộ trong phạm vi nội bộ hàm có thể để TypeScript tự suy luận (`type inference`).

```typescript
// SAI: Không khai báo kiểu trả về cho hàm export
export function calculateDiscount(price: number, percent: number) {
  return price * (percent / 100);
}

// ĐÚNG: Khai báo đầy đủ
export function calculateDiscount(price: number, percent: number): number {
  return price * (percent / 100);
}
```

### B. Interface vs. Type Alias
- Sử dụng `interface` cho cấu trúc dữ liệu đối tượng (Object shapes, Model, Database schemas) có thể mở rộng (`extends`).
- Sử dụng `type` cho Union types, Intersections, Mapped types, Tuples, hoặc Primitive aliases.
- Ưu tiên String Literal Union thay vì `enum` (để tránh rác bundle và dễ tương thích với JSON/Supabase):

```typescript
// Ưu tiên:
export type OrderStatus = 'pending' | 'processing' | 'completed' | 'cancelled';

// Thay vì:
// export enum OrderStatus { ... }
```

---

## 3. React & Component Props

- Định nghĩa Props thông qua `interface` hoặc `type` có tên riêng rõ ràng (ví dụ: `[ComponentName]Props`).
- Khai báo kiểu tường minh cho callback props.
- Tránh dùng `React.FC` nếu không cần thiết; dùng cú pháp hàm chuẩn:

```typescript
interface MomentCardProps {
  id: string;
  title: string;
  createdAt: string;
  isFavorite?: boolean;
  onSelect: (id: string) => void;
}

export function MomentCard({ id, title, isFavorite = false, onSelect }: MomentCardProps) {
  return (
    <div onClick={() => onSelect(id)}>
      <h3>{title}</h3>
    </div>
  );
}
```

---

## 4. Error Handling & Async Code

- Trong khối `catch (error)`, biến `error` luôn có kiểu `unknown`.
- Phải kiểm tra `if (error instanceof Error)` trước khi truy cập `error.message`.
- Mọi hàm `async` phải có return type `Promise<T>`.

```typescript
export async function fetchUserData(userId: string): Promise<UserData> {
  try {
    const res = await api.get(`/users/${userId}`);
    return res.data;
  } catch (error: unknown) {
    if (error instanceof Error) {
      throw new Error(`Failed to fetch user: ${error.message}`);
    }
    throw new Error('An unexpected error occurred while fetching user data');
  }
}
```

---

## 5. Discriminated Unions cho Async States

Khi quản lý trạng thái tải dữ liệu, ưu tiên dùng Discriminated Union thay vì nhiều cờ boolean (`isLoading`, `isError`, `data`) nằm cạnh nhau:

```typescript
type AsyncState<T> =
  | { status: 'idle'; data: null; error: null }
  | { status: 'loading'; data: null; error: null }
  | { status: 'success'; data: T; error: null }
  | { status: 'error'; data: null; error: Error };
```
