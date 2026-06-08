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
figureCaption: 'Giao diện sử dụng Shadcn Components'
---

### Interface using Shadcn Components

---

hideInToc: true
---

### Advantages & Disadvantages

<br/>

#### Advantages ✅

- **Accessibility** — built-in via Radix UI (keyboard nav, focus management, ARIA)
- **Fully customizable** — copy code, modify directly, no API lock-in
- **Tree-shakeable** — only bundle components you import
- **Flexible theming** — CSS variables for easy dark/light mode
- **Version updates** — CLI update command available

#### Disadvantages ❌

- **Missing complex components** — table, tree view, data grid must be built manually
- **Bundle size** — depends on number of components used
- **Radix dependency** — API changes require component updates
- **Not a traditional library** — developers need to understand structure for deep customization

<!--
Ưu điểm: Accessibility nhờ Radix UI, customizable hoàn toàn, tree-shakeable, theming linh hoạt qua CSS variables, có CLI update.
Nhược điểm: Không có sẵn complex components, bundle size phụ thuộc số components, phụ thuộc Radix UI API, không phải library truyền thống — dev cần hiểu cấu trúc.
-->
