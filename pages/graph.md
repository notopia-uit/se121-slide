---
layout: center
class: text-center
transition: slide-up
---

# Graph Visualization

---
hideInToc: true
layout: figure-side
figureUrl: quartz-logo.png
figureCaption: 'Quartz - Inspiration for Notopia Graph'
---

### Nguồn cảm hứng: Quartz

- **Quartz** ([github.com/jackyzha0/quartz](https://github.com/jackyzha0/quartz)) — static site generator cho digital garden
- Graph module trong Quartz được viết bằng **CommonJS + inline script**
- Team đã **port sang React component** với đầy đủ type safety và hooks
- Giữ nguyên core rendering: **D3 force simulation + Pixi.js**

---
hideInToc: true
---

### Tech Stack & Cách hoạt động

| Layer     | Library                       | Vai trò                                      |
| --------- | ----------------------------- | -------------------------------------------- |
| Layout    | **D3.js** (`forceSimulation`) | Tính toán vị trí node (force-directed graph) |
| Rendering | **Pixi.js**                   | Render đồ họa WebGL/WebGPU — hiệu suất cao   |
| Animation | **@tweenjs/tween.js**         | Tween mượt cho node/label opacity khi hover  |
| Input     | **D3 Drag + Zoom**            | Kéo thả node, zoom/Pan canvas                |

**Luồng render:**

1. D3 tính toán force layout → tọa độ node/link
2. Pixi.js vẽ canvas từ tọa độ D3
3. Animation loop cập nhật position mỗi frame
4. Tween.js xử lý hiệu ứng hover/focus

---
hideInToc: true
---

### Tính năng nổi bật

- **Depth control** — giới hạn số "bước" từ node trung tâm (local graph)
- **Drag & Zoom** — kéo node, zoom canvas (D3 zoom identity)
- **Hover highlight** — làm nổi bật node và link lân cận
- **Tag filtering** — ẩn/hiện tag nodes, danh sách tags bỏ qua
- **Radial layout** — tùy chọn bố trí hình tròn
- **Theme-aware** — đọc CSS variables, chuyển sang hex cho Pixi.js
- **Click navigation** — click node → chuyển trang
- **Visited tracking** — đánh dấu node đã xem qua localStorage

---
hideInToc: true
---

### Port từ Quartz (CommonJS) sang React

| Quartz (gốc)                             | Notopia (React)                                      |
| ---------------------------------------- | ---------------------------------------------------- |
| `graph.inline.ts` chạy sau DOM load      | `graph-render.ts` thuần function, gọi từ `useEffect` |
| Dùng `data-cfg` attribute + `JSON.parse` | Config là `D3Config` type, truyền qua props          |
| `window.spaNavigate` cho click           | `onNodeClick` callback prop                          |
| `fetchData` global variable              | Data là `GraphData` từ React Query                   |
| Không cleanup lifecycle                  | Cleanup function trong `useEffect` return            |

---
hideInToc: true
layout: figure
figureUrl: ui-graph-page.png
figureCaption: 'Giao diện Graph'
---

### Giao diện Graph

---
hideInToc: true
---

### Ưu & Nhược điểm

<br/>

#### Ưu điểm ✅

- **Hiệu suất cao** — Pixi.js WebGL render, phù hợp với hàng trăm node
- **Force layout tự nhiên** — D3 simulation giúp bố trí node trực quan
- **Tương tác phong phú** — drag, zoom, hover, click navigation
- **Theme-aware** — tự động theo dark/light mode qua CSS variables
- **Tái sử dụng** — Graph component dùng được cho cả local graph và global graph

#### Nhược điểm ❌

- **Phụ thuộc 3 thư viện nặng** — D3, Pixi.js, Tween.js (bundle size lớn)
- **GPU requirement** — Pixi.js cần WebGL/WebGPU support
- **Không responsive hoàn toàn** — cần resize handling
- **Phức tạp** — maintenance khó do nhiều layer rendering
- **Memory leak risk** — Pixi.js Application và animation loop cần cleanup kỹ
