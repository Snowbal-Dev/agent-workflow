# 📜 Rules Directory — Hệ Thống Quy Tắc Cốt Lõi

> **For AI Agents & Humans**: Skills tell you *how to do specific tasks*. 
> **Rules are the Constitution** that tells you *how you must think, code, and behave at all times*.
> Rules are non-negotiable and take precedence over default model behaviors.

---

## 🏛️ Danh Mục Quy Tắc (Rules Catalog)

### 1. `disciplined-reasoning.md` (Cẩm Nang Tư Duy Kỷ Luật & Karpathy)
Bao gồm 2 phần nền tảng:
- **Phần I: 7-Stage Operating Principles**:
  - **STAGE 0 — Clarify**: Tuyệt đối không suy đoán khi yêu cầu còn mơ hồ.
  - **STAGE 1 — Reasoning**: Trình bày chuỗi suy luận có cấu trúc.
  - **STAGE 2 — Multi-Options**: Luôn đề xuất 2-3 giải pháp khả thi với ưu/nhược điểm.
  - **STAGE 3 — Solution Choice**: Chọn phương án tối ưu và giải thích lý do.
  - **STAGE 4 — Execution**: Viết mã nguồn sạch, chuẩn mực, có xử lý lỗi.
  - **STAGE 5 — Self-Testing**: Chạy thử nghiệm giả định (dry-run) và đối soát test case.
  - **STAGE 6 — Conclusion**: Tóm tắt kết quả, giới hạn còn lại và hướng tiếp theo.
  - **7 Quy tắc bất biến**: Không bỏ qua Stage 0, không bịa đặt, nói tiếng Việt.
- **Phần II: Karpathy Guidelines (Kỷ Luật Lập Trình Andrej Karpathy)**:
  1. *Think Before Coding*: Dừng lại khi mơ hồ, chất vấn yêu cầu vô lý.
  2. *Simplicity First*: Triệt tiêu trừu tượng thừa, không over-engineering.
  3. *Surgical Changes*: Can thiệp chính xác như dao mổ phẫu thuật, không sửa lan man.
  4. *Goal-Driven Execution*: Biến mọi nhiệm vụ thành mục tiêu có thể kiểm chứng.

### 2. `typescript.md` (Quy Chuẩn Chống Gian Lận TypeScript Strict)
- **Cấm hoàn toàn `any`**: Sử dụng `unknown` và Type Narrowing an toàn.
- **Cấm ép kiểu mù quáng**: Cấm `as any`, `as unknown as T`.
- **Cấm che giấu lỗi compiler**: Tuyệt đối cấm `// @ts-ignore` hoặc `// @ts-nocheck`.
- **Interface & Types chuẩn**: Exported functions bắt buộc có kiểu trả về (`return type`).
- **Discriminated Unions**: Áp dụng cho async states (`idle | loading | success | error`).
- **Error Handling an toàn**: `catch (error: unknown)` kết hợp `instanceof Error`.

### 3. Thư mục `typescript/` (Quy Chuẩn Chi Tiết)
- **`coding-style.md`**: Chuẩn định dạng, đặt tên biến, tách object shapes.
- **`hooks.md`**: Tự động chạy Prettier format, tsc type check, cảnh báo `console.log`.
- **`patterns.md`**: Chuẩn hóa định dạng `ApiResponse<T>`, repository pattern.
- **`security.md`**: Quản lý bí mật môi trường (Environment variables), cấm hardcode credentials.
- **`testing.md`**: Tiêu chuẩn kiểm thử Playwright E2E và Vitest unit test.

---

## 🔌 Cơ Chế Tự Động Nạp Rules (How Rules are Loaded)

- **Antigravity / Gemini**: Tự động quét từ thư mục `.agents/rules/` và file `GEMINI.md`.
- **Claude Code**: Đọc qua cấu hình trong `CLAUDE.md`.
- **Cursor IDE & Windsurf**: Tự động áp dụng qua `.cursorrules` và `.windsurfrules`.
- **Codex / GPT-4o**: Nạp thông qua file tối cao `AGENTS.md`.