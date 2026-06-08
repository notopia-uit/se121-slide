---
layout: center
class: text-center
transition: slide-up
---

# Common Components

---
hideInToc: true
---

### Thư viện Shadcn UI

- **Shadcn UI** là bộ sưu tập components tái sử dụng, built trên **Radix UI** + **Tailwind CSS**
- Không phải package — copy code trực tiếp vào project, toàn quyền custom
- Dùng cho hầu hết UI components trong app: Button, Input, Dialog, Context Menu, Command, Sheet, ...
- Hỗ trợ **server component**, **dark mode**, **theming** qua CSS variables

---
hideInToc: true
layout: figure
figureUrl: ui-landing-page.png
figureCaption: 'Giao diện sử dụng Shadcn Components'
---

### Giao diện sử dụng Shadcn Components

---
hideInToc: true
---

### Ưu & Nhược điểm

<br/>

#### Ưu điểm ✅

- **Accessibility** sẵn có nhờ Radix UI (keyboard nav, focus management, ARIA)
- **Customizable** hoàn toàn — copy code, sửa trực tiếp, không bị lock vào API
- **Tree-shakeable** — chỉ bundle components được import
- **Theming linh hoạt** qua CSS variables, dễ dàng dark/light mode
- **Cập nhật theo version** — có CLI update command

#### Nhược điểm ❌

- **Không có sẵn** complex components (table, tree view, data grid) — phải tự build
- **Bundle size** phụ thuộc vào số components dùng (dù chỉ copy code cần thiết)
- **Phụ thuộc vào Radix UI** — nếu Radix thay đổi API, components phải update theo
- **Không phải component library truyền thống** — dev cần hiểu cấu trúc để custom sâu
