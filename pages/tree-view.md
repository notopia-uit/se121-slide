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

- **Drag & Drop**
- **Rename**
- **Search**
- **Context Menu**
- **Keyboard Navigation**
- **Auto Expand**
- **Real-time sync**

<!--
Drag & Drop: kéo thả folder/note giữa các thư mục. Rename: inline rename với context menu. Search: tìm kiếm node theo tên, auto expand path. Context Menu: New Note, New Folder, Move to Trash. Keyboard Navigation: arrow keys, Enter để mở note. Auto Expand: expand parent khi tạo item mới. Real-time sync: subscribe workspace events → invalidate query.
-->

---
hideInToc: true
---

### Advantages & Disadvantages

<br/>

#### Advantages ✅

- **Feature-rich API**
- **Flexible custom render**
- **Controlled/Uncontrolled**
- **TreeDataProvider**
- **TypeScript compatible**

#### Disadvantages ❌

- **Not Shadcn compatible**
- **Bundle size**
- **Low popularity**
- **Learning curve**
- **Accessibility**

<!--
Advantages: API giàu tính năng — drag & drop, rename, search, keyboard nav out-of-the-box. Custom render linh hoạt — renderItem, renderItemArrow cho phép styling tùy ý. Hỗ trợ cả Controlled và Uncontrolled mode. TreeDataProvider cho phép async load data, lazy loading. Full TypeScript type safety.

Disadvantages: Không compatible với Shadcn — phải dùng ControlledTreeEnvironment thay vì Shadcn styling thuần. Bundle size ~15-20kB gzipped. Thư viện ít phổ biến, ít contributor. ControlledTreeEnvironment API khá phức tạp — learning curve cao. Accessibility không mạnh bằng Radix UI components.
-->
