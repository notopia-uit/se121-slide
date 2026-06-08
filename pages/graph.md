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

### Inspiration: Quartz

- **Quartz** ([github.com/jackyzha0/quartz](https://github.com/jackyzha0/quartz)) — static site generator for digital gardens
- Graph module written in **CommonJS + inline script**
- **Ported to React** with full type safety and hooks
- Core rendering unchanged: **D3 force simulation + Pixi.js**

<!--
Quartz là nguồn cảm hứng chính cho Graph. Điểm mấu chốt: đã port từ inline script CommonJS sang React component, giữ core rendering là D3 + Pixi.js.
-->

---
hideInToc: true
---

### Tech Stack & How It Works

| Layer     | Library                       | Role                                           |
| --------- | ----------------------------- | ---------------------------------------------- |
| Layout    | **D3.js** (`forceSimulation`) | Computes node positions (force-directed graph) |
| Rendering | **Pixi.js**                   | WebGL/WebGPU graphics — high performance       |
| Animation | **@tweenjs/tween.js**         | Smooth tween for node/label opacity on hover   |
| Input     | **D3 Drag + Zoom**            | Node dragging, canvas zoom/pan                 |

**Render flow:** D3 calculates layout → Pixi.js draws canvas → animation loop updates each frame → Tween.js handles hover effects

<!--
4 layer: Layout (D3), Render (Pixi.js), Animation (Tween.js), Input (D3 Drag/Zoom).
Luồng render: D3 tính toán → Pixi.js vẽ → animation loop cập nhật → Tween.js xử lý hover.
-->

---
hideInToc: true
---

### Key Features

- **Depth control** — limit steps from center node
- **Drag & Zoom** — move nodes, zoom canvas
- **Hover highlight** — highlight adjacent nodes and links
- **Tag filtering** — show/hide tag nodes
- **Radial layout** — circular arrangement option
- **Theme-aware** — reads CSS variables for Pixi.js
- **Click navigation** — click node to navigate
- **Visited tracking** — marks viewed nodes via localStorage

<!--
Depth control giới hạn số bước từ node trung tâm. Drag & Zoom kéo node, zoom canvas. Hover highlight làm nổi bật node và link lân cận. Theme-aware tự động đọc CSS variables cho Pixi.js.
-->

---
hideInToc: true
---

### Port from Quartz (CommonJS → React)

| Quartz (original)                        | Notopia (React)                                      |
| ---------------------------------------- | ---------------------------------------------------- |
| `graph.inline.ts` runs after DOM load    | `graph-render.ts` pure function, called from `useEffect` |
| `data-cfg` attribute + `JSON.parse`      | Typed `D3Config` config, passed via props            |
| `window.spaNavigate` for click           | `onNodeClick` callback prop                          |
| `fetchData` global variable              | `GraphData` from React Query                         |
| No cleanup lifecycle                     | Cleanup function in `useEffect` return               |

<!--
Điểm quan trọng: cleanup lifecycle — useEffect return cleanup function để tránh memory leak từ Pixi.js Application và animation loop.
-->

---
hideInToc: true
layout: figure
figureUrl: ui-graph-page.png
figureCaption: 'Giao diện Graph'
---

### Graph Interface

---

hideInToc: true
---

### Advantages & Disadvantages

<br/>

#### Advantages ✅

- **High performance** — Pixi.js WebGL handles hundreds of nodes
- **Natural force layout** — D3 simulation creates intuitive arrangement
- **Rich interaction** — drag, zoom, hover, click navigation
- **Theme-aware** — automatic dark/light mode via CSS variables
- **Reusable** — single Graph component for local and global graphs

#### Disadvantages ❌

- **3 heavy libraries** — D3, Pixi.js, Tween.js (large bundle size)
- **GPU requirement** — Pixi.js needs WebGL/WebGPU support
- **Not fully responsive** — requires manual resize handling
- **Complex maintenance** — multiple rendering layers
- **Memory leak risk** — Pixi.js Application and animation loop need careful cleanup

<!--
Ưu điểm: WebGL hiệu suất cao, D3 force layout trực quan, tương tác phong phú, theme-aware, tái sử dụng được.
Nhược điểm: 3 thư viện nặng, cần GPU, không responsive hoàn toàn, maintenance khó, nguy cơ memory leak.
-->
