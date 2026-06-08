---
layout: center
class: text-center
transition: slide-up
---

## Editor

---
hideInToc: true
layout: figure-side
figureUrl: yjs-logo.svg
figureCaption: Yjs Logo
---

### Yjs

- A powerful CRDT library for JavaScript, specializing in real-time collaborative applications.
- Architecture centers around a **Y.Doc** (the central document), **Shared Data Types** (Array, Map, Text, XML), and **Providers** (network connections).
- Offers utilities like an **Undo/Redo Manager** and **Awareness** (for sharing cursor positions, user info).
- Advantages: High performance, offline-first, and a vast ecosystem of editor bindings and providers.
- Disadvantages: Higher memory consumption due to storing metadata for each data element.

<!--
Yjs đóng vai trò là "lõi" của tính năng cộng tác, giúp việc đồng bộ hóa dữ liệu trở nên đơn giản và tin cậy.
Yjs implement theo thuật toán YATA (Yet Another Transformation Approach)

Khi làm việc với Yjs, mình thao tác với YDoc, Shared Data Types (Array, Map, Text, XML), và Providers (WebSocket, WebRTC, etc.) để đồng bộ hóa dữ liệu giữa các client.

Yjs tốn bộ nhớ hơn so với các giải pháp khác, nhưng thực sự không đáng lo ngại (có bài blog so sánh, benchmark).

Yjs insert là operation based CDRT, nhưng delete là state based CRDT. Được mark là đã bị xoá, và được garbage collector xoá sau một thời gian.
-->

---
hideInToc: true
layout: figure-side
figureUrl: prosemirror-logo.svg
figureCaption: ProseMirror Logo
---

## ProseMirror

- A low-level toolkit for building rich text editors.
- Uses a strict, structured **Document Model** instead of free-form HTML, enabling precise content control.
- Comprises four core libraries: **Model** (defines the schema), **State** (manages state), **View** (renders the UI), and **Transform** (handles change steps).
- It is the foundation for many modern editors and serves as a binding layer for Yjs.

<!--
ProseMirror cung cấp nền tảng cho việc xử lý văn bản, đảm bảo dữ liệu luôn hợp lệ theo cấu trúc đã định nghĩa.

Làm việc với ProseMirror sẽ thao tác với Document Model (Node, Mark), State (EditorState), View (EditorView), và Transform (Step, Transaction) để quản lý và cập nhật nội dung.

ProseMirror đã chuyển source code từ github sang https://code.haverbeke.berlin/prosemirror/

Bên cạnh ProseMirror, còn có một số thư viện khác như Slate, Quill, Lexical bởi Meta,
nhưng tiptap sử dụng ProseMirror làm nền tảng, và BlockNote sử dụng Tiptap.
-->

---
hideInToc: true
layout: figure-side
figureUrl: tiptap-logo.svg
figureCaption: Tiptap Logo
---

## Tiptap

- A "headless" editor framework built on top of ProseMirror.
- Provides a higher level of abstraction, making it easier for developers to use through its **Extension**, **Command**, and **Event** system.
- Offers excellent support for modern UI frameworks like React and Vue.
- Includes a built-in collaboration extension for Yjs and provides smoother state management than vanilla ProseMirror.

<!--
Headless có nghĩa là Tiptap không đi kèm với giao diện người dùng mặc định,
cho phép các nhà phát triển tự do thiết kế trải nghiệm người dùng của riêng họ.

Tiptap cung cấp một hệ thống Extension để mở rộng tính năng, Command để thao tác với editor state, và Event để lắng nghe các sự kiện trong editor.

Các extension là bọc lại các Node, Mark, hoặc Plugin của ProseMirror; abstract Prosemirror.
-->

---
hideInToc: true
---

## Hocuspocus

- A dedicated WebSocket server for Yjs, acting as the collaboration backend.
- Manages client connections, user authentication, and data persistence.
- Its flexible extension system supports various databases (SQLite, PostgreSQL, S3) and scaling solutions (Redis).
- Supports features like Webhooks and automatic data storage.

<!--
Hocuspocus là giải pháp collab bởi Tiptap team.
Hocuspocus giải quyết bài toán hạ tầng backend, giúp việc triển khai máy chủ cộng tác trở nên nhanh chóng và chuyên nghiệp.

Hocuspocus có hệ thống extension linh hoạt, cho phép tích hợp với nhiều loại cơ sở dữ liệu (data được lưu là YDoc binary là chủ yếu) và giải pháp scale khác nhau.
-->

---
hideInToc: true
---

## Tiptap - Free vs. Paid

- **Tiptap Cloud (Paid/Managed):**
  - **Infrastructure as a Service:** Fully managed scaling, Redis for high availability, and S3/PostgreSQL persistence.
  - **Pro Extensions:** Access to **Snapshots (Versioning)**, **Comments**, **File Conversion** (DOCX, PDF), and **Unique ID**.
  - **Developer APIs:** Includes a **REST Document API** and **Webhooks** for event-driven backend integration.
  - **AI Toolkit:** Integrated AI-powered editing (generation, summarization, etc.) as a paid add-on.
- **Hocuspocus Self-hosted (Free Core):**
  - **Full Control:** We own the data and infrastructure, but must manage WebSocket scaling and security ourselves.
  - **License Constraints:** Pro extensions mentioned above require a commercial license even if self-hosting.
  - **Operational Overhead:** Requires manual setup for persistence (SQLite/Postgres), monitoring, and server updates.

<!--
Tiptap Cloud (Trả phí):
- Infrastructure as a Service: Họ lo toàn bộ việc scale, Redis, và lưu trữ dữ liệu (S3/Postgres).
- Pro Extensions: Có sẵn các tính năng cao cấp như Versioning (Snapshots), Comments, và Export/Import file.
- APIs & Webhooks: Cung cấp REST API để thao tác với document từ backend và Webhooks để nhận thông báo sự kiện.
- AI Toolkit: Tích hợp sẵn các tính năng AI (viết bài, tóm tắt) dưới dạng add-on trả phí.

Hocuspocus Self-hosted (Miễn phí core):
- Quyền kiểm soát: Mình tự quản lý data và hạ tầng, nhưng phải tự lo việc scale WebSocket và bảo mật.
- Giới hạn License: Các extension Pro vẫn yêu cầu license thương mại kể cả khi tự host.
- Gánh nặng vận hành: Phải tự cài đặt persistence, monitor server và cập nhật phiên bản thủ công.
-->

---
hideInToc: true
layout: figure-side
figureUrl: blocknote-logo.svg
figureCaption: BlockNote Logo
---

## BlockNote

- A modern, **block-based** text editor inspired by Notion.
- Built on top of Tiptap and ProseMirror, and optimized for React.
- Features a simple data model: a document is a list of blocks (paragraph, image, table, etc.).
- Comes ready for real-time collaboration and is easily stylable with libraries like shadcn/ui.

<!--
BlockNote cung cấp trải nghiệm người dùng cuối (UX) với giao diện dạng khối,
đồng thời kế thừa toàn bộ sức mạnh công nghệ từ các lớp bên dưới.
-->

---
hideInToc: true
layout: two-cols
---

### BlockNote - Example Blocks

```json
[
  {
    "type": "paragraph",
    "content": "Welcome to this demo!"
  },
  {
    "type": "quote",
    "content": "Quote"
  },
  {
    "type": "bulletListItem",
    "content": "Bullet List Item"
  }
]
```

::right::

```json
[
  {
    "type": "table",
    "content": {
      "type": "tableContent",
      "rows": [
        {
          "cells": [
            "Table Cell",
            "Table Cell",
            "Table Cell"
          ]
        },
        {
          "cells": [
            "Table Cell",
            "Table Cell",
            "Table Cell"
          ]
        }
      ]
    }
  }
]
```

---
hideInToc: true
layout: figure-side
figureUrl: blocknote-intro-example.png
---

### BlockNote - Example Blocks - Continue

```json
[
  {
    "type": "image",
    "props": {
      "url": "https://placehold.co/332x322.jpg",
      "caption": "From https://placehold.co/332x322.jpg"
    }
  },
  {
    "type": "paragraph",
    "content": [
      {
        "type": "text",
        "text": "Styled Text",
        "styles": {
          "bold": true,
          "italic": true,
          "textColor": "red",
          "backgroundColor": "blue"
        }
      },
      {
        "type": "link",
        "content": "Link",
        "href": "https://www.blocknotejs.org"
      }
    ]
  }
]
```
