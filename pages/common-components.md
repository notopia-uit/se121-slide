---
layout: center
class: text-center
transition: slide-up
---

# Common Components

---
hideInToc: true
---

### Shadcn UI

- A collection of reusable components built on **Radix UI** + **Tailwind CSS**
- Not a package — copy code directly into project, full customization control
- Used for most UI components: **Button**, **Input**, **Dialog**, **Context Menu**, **Command**, **Sheet**, ...
- Supports **server components**, **dark mode**, **theming** via CSS variables

<!--
Shadcn UI built trên Radix UI + Tailwind CSS. Không phải package — copy code trực tiếp vào project, toàn quyền custom. Hỗ trợ server component, dark mode, theming qua CSS variables.
-->

---
hideInToc: true
layout: figure
figureUrl: ui-landing-page.png
figureCaption: 'Interface built with Shadcn UI components'
---

---
hideInToc: true
---

### Advantages & Disadvantages

<br/>

#### Advantages ✅

- **Accessibility**
- **Fully customizable**
- **Tree-shakeable**
- **Flexible theming**
- **Version updates**

#### Disadvantages ❌

- **Missing complex components**
- **Bundle size**
- **Radix dependency**
- **Not a traditional library**

<!--
Advantages: Accessibility sẵn có nhờ Radix UI (keyboard nav, focus management, ARIA). Customizable hoàn toàn — copy code, sửa trực tiếp, không bị lock vào API. Tree-shakeable — chỉ bundle components được import. Theming linh hoạt qua CSS variables, dễ dàng dark/light mode. Có CLI update command.

Disadvantages: Không có sẵn complex components (table, tree view, data grid) — phải tự build. Bundle size phụ thuộc vào số components dùng. Phụ thuộc vào Radix UI — nếu Radix thay đổi API, components phải update theo. Không phải component library truyền thống — dev cần hiểu cấu trúc để custom sâu.
-->
