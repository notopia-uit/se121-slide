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

### Port from Quartz (CommonJS → React)

| Quartz (original)                     | Notopia (React)                                          |
| ------------------------------------- | -------------------------------------------------------- |
| `graph.inline.ts` runs after DOM load | `graph-render.ts` pure function, called from `useEffect` |
| `data-cfg` attribute + `JSON.parse`   | Typed `D3Config` config, passed via props                |
| `window.spaNavigate` for click        | `onNodeClick` callback prop                              |
| `fetchData` global variable           | `GraphData` from React Query                             |
| No cleanup lifecycle                  | Cleanup function in `useEffect` return                   |

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

- **High performance**
- **Natural force layout**
- **Rich interaction**
- **Theme-aware**
- **Reusable**

#### Disadvantages ❌

- **3 heavy libraries**
- **GPU requirement**
- **Not fully responsive**
- **Complex maintenance**
- **Memory leak risk**

<!--
Advantages: Pixi.js WebGL render hiệu suất cao, phù hợp hàng trăm node. D3 simulation giúp bố trí node trực quan. Tương tác phong phú: drag, zoom, hover, click navigation. Theme-aware tự động theo dark/light mode qua CSS variables. Graph component dùng được cho cả local graph và global graph.

Disadvantages: Phụ thuộc 3 thư viện nặng (D3, Pixi.js, Tween.js) — bundle size lớn. Pixi.js cần WebGL/WebGPU support. Không responsive hoàn toàn, cần resize handling. Maintenance khó do nhiều layer rendering. Pixi.js Application và animation loop cần cleanup kỹ — nguy cơ memory leak.
-->
