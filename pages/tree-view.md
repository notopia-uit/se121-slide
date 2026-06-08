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

- **react-complex-tree** — thư viện tree view cho React, hỗ trợ đầy đủ drag & drop, keyboard nav, search
- Shadcn UI **không có** File Tree component — issue [#355](https://github.com/shadcn-ui/ui/issues/355)
- react-complex-tree **không tương thích** với Shadcn styling mặc định
- Giải pháp: dùng **ControlledTreeEnvironment** để custom render

---
hideInToc: true
---

### ControlledTreeEnvironment — Code Example

```tsx
<ControlledTreeEnvironment<string>
  items={items}
  getItemTitle={(item) => item.data}
  canDragAndDrop={true}
  canReorderItems={true}
  canDropOnFolder={true}
  canRename={true}
  viewState={viewState}
  onDrop={onDrop}
  onRenameItem={(item, name) => {
    /* rename logic */
  }}
  renderItem={({ title, item, arrow, context, depth, children }) => (
    <li {...context.itemContainerWithChildrenProps}>
      <Button
        {...context.interactiveElementProps}
        style={{
          paddingLeft: `${item.isFolder ? depth * 10 : depth * 10 + 16}px`,
        }}
      >
        {item.isFolder && arrow}
        {title}
      </Button>
      {children}
    </li>
  )}
>
  <Tree treeId="tree-sample" rootItem={rootId} treeLabel="Tree" />
</ControlledTreeEnvironment>
```

- **ControlledTreeEnvironment** — wrapper quản lý state tree tập trung
- `renderItem`, `renderItemArrow`, `renderItemTitle` — custom render functions
- Kết hợp Shadcn `Button`, `ContextMenu` để styling đồng bộ

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

```ts
// Map từ API response sang TreeData
const mapDtoTreeData = (rootFolder: NoteWorkspaceTreeFolder) => {
  const tree: TreeData = {};
  const traverse = (node, isFolder) => {
    tree[node.id] = { index: node.id, data: node.name, isFolder };
    if (isFolder) node.children?.forEach((c) => traverse(c, true));
  };
  traverse(rootFolder, true);
  return { treeData: tree, rootId: rootFolder.id };
};
```

---
hideInToc: true
---

### TreeView Features

- **Drag & Drop** — kéo thả folder/note giữa các thư mục
- **Rename** — inline rename với context menu
- **Search** — tìm kiếm node theo tên, auto expand path
- **Context Menu** — New Note, New Folder, Move to Trash
- **Keyboard Navigation** — arrow keys, Enter để mở note
- **Auto Expand** — expand parent khi tạo item mới
- **Real-time sync** — subscribe workspace events → invalidate query

---
hideInToc: true
layout: figure
figureUrl: ui/workspace-page.png
figureCaption: 'Giao diện Tree View'
---

### Giao diện Tree View

---
hideInToc: true
---

### Ưu & Nhược điểm

<br/>

#### Ưu điểm ✅

- **API giàu tính năng** — drag & drop, rename, search, keyboard nav out-of-the-box
- **Custom render linh hoạt** — `renderItem`, `renderItemArrow` cho phép styling tùy ý
- **Controlled/Uncontrolled** — hỗ trợ cả 2 mode
- **TreeDataProvider** — có thể async load data, lazy loading
- **Tương thích TypeScript** — full type safety

#### Nhược điểm ❌

- **Không compatible với Shadcn** — must use `ControlledTreeEnvironment` thay vì Shadcn styling thuần
- **Bundle size** — ~15-20kB gzipped
- **Maintenance** — thư viện ít phổ biến, ít contributor
- **Learning curve** — ControlledTreeEnvironment API khá phức tạp
- **Accessibility** — không mạnh bằng Radix UI components
