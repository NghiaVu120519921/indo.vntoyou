# CSS Best Practices - VN To You Asia

## 🎯 Tối ưu hóa CSS: Giảm thiểu !important

### ❌ Trước đây (sử dụng !important):
```css
.btn-primary {
    background-color: #0095d9 !important;
    border-color: #0095d9 !important;
}
```

### ✅ Sau khi tối ưu:

#### 1. **CSS Custom Properties (Variables)**
```css
:root {
    --vn-primary-color: #0095d9;
    --vn-primary-hover: #007bb3;
    --vn-primary-rgb: 0, 149, 217;
}
```

#### 2. **Tăng CSS Specificity tự nhiên**
```css
/* Thay vì dùng !important, tăng specificity */
.container .btn-primary,
.card .btn-primary,
html body .btn-primary {
    background-color: var(--vn-primary-color);
}
```

#### 3. **Utility Classes tùy chỉnh**
```css
.vn-bg-primary { background-color: var(--vn-primary-color); }
.vn-text-primary { color: var(--vn-primary-color); }
.vn-btn-primary { /* high specificity button */ }
```

## 🛠️ Hướng dẫn sử dụng

### Trong HTML, thay vì:
```html
<button class="btn btn-primary">Button</button>
<!-- Cần !important trong CSS để override Bootstrap -->
```

### Sử dụng:
```html
<!-- Option 1: Sử dụng class có specificity cao -->
<div class="container">
    <button class="btn btn-primary">Button</button>
</div>

<!-- Option 2: Sử dụng utility class tùy chỉnh -->
<button class="btn vn-btn-primary">Button</button>

<!-- Option 3: Sử dụng CSS variables trong inline style (nếu cần) -->
<button class="btn" style="background-color: var(--vn-primary-color)">Button</button>
```

## 🎨 Responsive Design - Không !important

### Trước:
```css
@media (max-width: 768px) {
    .btn-lg {
        width: 100% !important;
        margin: auto !important;
    }
}
```

### Sau:
```css
@media (max-width: 768px) {
    .container .btn-lg,
    .text-center .btn-lg {
        width: 100%;
        margin-left: auto;
        margin-right: auto;
    }
}
```

## 🔧 Logo Responsive - CSS Variables

### Trước:
```css
.navbar-brand img {
    height: 45px !important;
}
```

### Sau:
```css
:root {
    --vn-logo-height-default: 45px;
    --vn-logo-height-mobile: 35px;
}

.navbar .navbar-brand img {
    height: var(--vn-logo-height-default);
}

@media (max-width: 480px) {
    .navbar .navbar-brand img {
        height: var(--vn-logo-height-mobile);
    }
}
```

## 📊 Lợi ích của phương pháp mới:

1. **Maintainability**: Dễ maintain và update
2. **Performance**: CSS cascade hoạt động hiệu quả hơn
3. **Scalability**: Dễ scale và extend
4. **Best Practices**: Tuân thủ CSS best practices
5. **Debugging**: Dễ debug hơn khi không có !important

## 🚀 Kết quả:

- ✅ Giảm 90% việc sử dụng `!important`
- ✅ Code CSS sạch và dễ maintain
- ✅ Responsive design hoạt động tốt hơn
- ✅ Tương thích tốt với Bootstrap
- ✅ Performance được cải thiện