---
name: liquid-glass-frosted
description: |
  Apple-style Liquid Glass / Frosted Glass effect cho bất kỳ element nào.
  Tạo hiệu ứng nền nhòe mờ + khúc xạ kiểu kính mờ Apple.
  Đã debug và xác nhận hoạt động trên Chrome, Safari, Firefox.
---

# Liquid Glass — Frosted Blur Effect

Hiệu ứng kính mờ Apple-style, nền content phía sau bị blur nhòe.

## Cách dùng nhanh

### 1. CSS Variables (đặt trên container cha)

```css
--glass-color: #bbbbbc;        /* Màu tint kính — xám cho neutral, hồng cho ấm */
--glass-light: #ffffff;
--glass-dark: #000000;
--glass-reflex-light: 1;       /* Cường độ phản chiếu sáng (0–1) */
--glass-reflex-dark: 1;        /* Cường độ phản chiếu tối (0–1) */
--glass-saturation: 160%;      /* Saturate cho backdrop */
```

Dark mode override:
```css
--glass-reflex-light: 0.35;
--glass-reflex-dark: 2;
```

### 2. Class chính — `.liquid-glass-surface`

```css
.liquid-glass-surface {
  background-color: color-mix(in srgb, var(--glass-color) 12%, transparent);
  backdrop-filter: blur(40px) saturate(var(--glass-saturation));
  -webkit-backdrop-filter: blur(40px) saturate(var(--glass-saturation));
  border-radius: 9999px; /* hoặc tuỳ shape */
  border: 0;
  box-shadow:
    /* Viền sáng bên trong — tạo cảm giác kính có chiều sâu */
    inset 0 0 0 1px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 10%), transparent),
    inset 1.8px 3px 0 -2px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 90%), transparent),
    inset -2px -2px 0 -2px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 80%), transparent),
    inset -3px -8px 1px -6px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 60%), transparent),
    /* Viền tối bên trong — tạo chiều sâu phía đối diện */
    inset -0.3px -1px 4px 0 color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 12%), transparent),
    inset -1.5px 2.5px 0 -2px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 20%), transparent),
    inset 0 3px 4px -2px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 20%), transparent),
    inset 2px -6.5px 1px -4px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 10%), transparent),
    /* Drop shadow */
    0 1px 5px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 10%), transparent),
    0 6px 16px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 8%), transparent);
  transition:
    background-color 400ms cubic-bezier(1, 0, 0.4, 1),
    box-shadow 400ms cubic-bezier(1, 0, 0.4, 1);
}
```

### 3. Pill indicator (cho tab switcher)

```css
.liquid-glass-pill {
  background-color: color-mix(in srgb, var(--glass-color) 36%, transparent);
  border-radius: 9999px;
  box-shadow:
    inset 0 0 0 1px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 10%), transparent),
    inset 2px 1px 0 -1px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 90%), transparent),
    inset -1.5px -1px 0 -1px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 80%), transparent),
    inset -2px -6px 1px -5px color-mix(in srgb, var(--glass-light) calc(var(--glass-reflex-light) * 60%), transparent),
    inset -1px 2px 3px -1px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 20%), transparent),
    inset 0 -4px 1px -2px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 10%), transparent),
    0 3px 6px color-mix(in srgb, var(--glass-dark) calc(var(--glass-reflex-dark) * 8%), transparent);
  transition:
    translate 440ms cubic-bezier(1, 0, 0.4, 1),
    background-color 400ms cubic-bezier(1, 0, 0.4, 1),
    box-shadow 400ms cubic-bezier(1, 0, 0.4, 1);
}
```

## ⚠️ CÁC BẪY PHẢI TRÁNH (đã debug xong)

### Bẫy 1: `transform` trên parent → giết chết backdrop-filter
```css
/* ❌ SAI — transform tạo containing-block, backdrop-filter chỉ blur
   nội dung TRONG wrapper, không blur content trang bên ngoài */
.wrapper {
  position: fixed;
  left: 50%;
  transform: translateX(-50%); /* THỦ PHẠM */
}
.wrapper .glass-child {
  backdrop-filter: blur(40px); /* KHÔNG HOẠT ĐỘNG */
}

/* ✅ ĐÚNG — căn giữa bằng margin, không dùng transform */
.wrapper {
  position: fixed;
  left: 0;
  right: 0;
  width: fit-content;
  margin-inline: auto;
  transform: none; /* QUAN TRỌNG */
}
```

### Bẫy 2: `viewTransitionName` trên parent → cũng giết backdrop-filter
```css
/* ❌ SAI */
<div style="viewTransitionName: 'my-nav'">
  <nav style="backdrop-filter: blur(40px)">  /* KHÔNG HOẠT ĐỘNG */

/* ✅ ĐÚNG — KHÔNG đặt viewTransitionName lên parent của element có backdrop-filter */
<div>
  <nav style="backdrop-filter: blur(40px)">  /* HOẠT ĐỘNG */
```

### Bẫy 3: background-color quá đặc → che mất hiệu ứng blur
```css
/* ❌ SAI — 65% opacity = gần như solid, blur bị che */
background-color: color-mix(in srgb, white 65%, transparent);

/* ✅ ĐÚNG — 12% opacity = trong suốt đủ để thấy blur */
background-color: color-mix(in srgb, var(--glass-color) 12%, transparent);
```

### Bẫy 4: SVG filter trong backdrop-filter gây co/méo
```css
/* ❌ SAI — SVG filter dùng objectBoundingBox primitiveUnits
   sẽ distort/co nội dung khi áp dụng qua backdrop-filter */
backdrop-filter: blur(40px) url(#my-svg-filter);

/* ✅ ĐÚNG — chỉ dùng CSS filter functions */
backdrop-filter: blur(40px) saturate(160%);
```

## Tuỳ chỉnh mức blur

| Mức blur  | Giá trị    | Dùng khi                          |
|-----------|------------|-----------------------------------|
| Nhẹ       | `blur(8px)` | Hint nhẹ, text vẫn đọc được     |
| Trung bình| `blur(20px)`| Frosted nhẹ, thấy hình dạng      |
| Mạnh      | `blur(40px)`| Frosted đậm (giống Apple)         |
| Cực mạnh  | `blur(80px)`| Hoàn toàn mờ, chỉ thấy màu sắc  |

## Nguồn gốc

Dựa trên bản gốc: `apple-liquid-glass-switcher` (CodePen)
- File tham chiếu: `C:\Users\Vit Zun\Downloads\apple-liquid-glass-switcher\apple-liquid-glass-switcher\src\style.css`
- Đã tuỳ chỉnh cho UsNote theme (hồng ấm thay vì xám trung tính)
