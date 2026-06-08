---
layout: center
class: text-center
transition: slide-up
---

# Tree View

---
hideInToc: true
layout: figure-side
figureUrl: rct-logo.svg
figureCaption: 'React Complex Tree - Thư viện Tree View cho React'
---

### react-complex-tree

- A React tree view library with full **drag & drop**, **keyboard nav**, **search**
- Shadcn UI **does not have** a File Tree component — [issue #355](https://github.com/shadcn-ui/ui/issues/355)
- **Not compatible** with Shadcn styling out of the box
- Solution: use **ControlledTreeEnvironment** for custom rendering

<!--
react-complex-tree là thư viện tree view. Shadcn không có File Tree component. Giải pháp: dùng ControlledTreeEnvironment để custom render, kết hợp Shadcn Button/ContextMenu cho styling đồng bộ.
-->

---
hideInToc: true
---

### ControlledTreeEnvironment

- Wrapper managing centralized tree state
- `renderItem`, `renderItemArrow`, `renderItemTitle` — custom render functions
- Combine with Shadcn `Button`, `ContextMenu` for consistent styling

<!--
ControlledTreeEnvironment là wrapper quản lý state tập trung. Các custom render functions cho phép styling tùy ý, kết hợp với Shadcn Button, ContextMenu.
-->

---
hideInToc: true
---

### Tree Data Model

```ts
type TreeData = Record<TreeItemIndex, TreeItem<string>>;

type TreeItem<T> = {
  index: TreeItemIndex;
  data: T;
  isFolder: boolean;
  children?: TreeItemIndex[];
};
```

- Map from API `NoteWorkspaceTreeFolder` → `TreeData`
- Recursive traversal builds flat tree structure

<!--
Model dữ liệu dạng flat: TreeData là Record, mỗi TreeItem có index, data, isFolder, children. mapDtoTreeData chuyển từ API response sang TreeData bằng duyệt đệ quy.
-->

---
hideInToc: true
---

### Key Features

- **Drag & Drop** — move folders/notes between directories
- **Rename** — inline rename via context menu
- **Search** — find nodes by name, auto-expand path
- **Context Menu** — New Note, New Folder, Move to Trash
- **Keyboard Navigation** — arrow keys, Enter to open
- **Auto Expand** — expand parent when creating items
- **Real-time sync** — subscribe workspace events → invalidate query

<!--
Drag & Drop kéo thả folder/note giữa các thư mục. Rename inline với context menu. Search tự động expand path. Real-time sync subscribe workspace events và invalidate query.
-->

---
hideInToc: true
layout: figure
figureUrl: ui/workspace-page.png
figureCaption: 'Giao diện Tree View'
---

### Tree View Interface

---

hideInToc: true
---

### Advantages & Disadvantages

<br/>

#### Advantages ✅

- **Feature-rich API** — drag & drop, rename, search, keyboard nav out of the box
- **Flexible custom render** — `renderItem`, `renderItemArrow` for custom styling
- **Controlled/Uncontrolled** — supports both modes
- **TreeDataProvider** — async data loading, lazy loading
- **TypeScript compatible** — full type safety

#### Disadvantages ❌

- **Not Shadcn compatible** — must use `ControlledTreeEnvironment`
- **Bundle size** — ~15-20kB gzipped
- **Low popularity** — fewer contributors, less community support
- **Learning curve** — ControlledTreeEnvironment API is complex
- **Accessibility** — weaker than Radix UI components

<!--
Ưu điểm: API giàu tính năng, custom render linh hoạt, hỗ trợ controlled/uncontrolled, có TreeDataProvider cho lazy loading, full TypeScript.
Nhược điểm: Không compatible với Shadcn, bundle size ~15-20kB, thư viện ít phổ biến, learning curve cao, accessibility không mạnh bằng Radix.
-->
