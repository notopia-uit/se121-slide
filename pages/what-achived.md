---
layout: center
class: text-center
transition: slide-up
---

# What Achieved

<!--
Đây là phần tổng kết về những gì nhóm đã đạt được trong suốt quá trình thực hiện đồ án.
-->

---
hideInToc: true
---

## Core Achievements

<CardRow :items="[
  {
    title: 'Complete Product',
    content: 'A note-taking system with real-time collaboration and workspace management',
    icon: 'i-carbon-application'
  },
  {
    title: 'Modern Architecture',
    content: 'Microservices using Go/NestJS, Event-Driven Architecture with Redpanda, and Contract-First API',
    icon: 'i-carbon-flow-data'
  },
  {
    title: 'Advanced Tooling',
    content: 'Nx Monorepo, Casbin RBAC models, and OIDC authentication via Authentik',
    icon: 'i-carbon-cloud-service-management'
  }
]" />

<!--
Về sản phẩm, nhóm đã hoàn thiện hệ thống với đầy đủ các tính năng như cộng tác thời gian thực, quản lý không gian làm việc.
Về kiến trúc, hệ thống được xây dựng theo mô hình Microservices, hỗ trợ Event-Driven và áp dụng Contract-First API giúp frontend/backend phát triển song song.
Sử dụng ngôn ngữ Go cho backend service note, trong khi NestJS cho các dịch vụ liên quan đến xử lý document, vi công nghệ BlockNote và các thư viện liên quan đến editor ở JS.
Nhóm cũng áp dụng các công cụ hiện đại như Nx Monorepo để quản lý code và Authentik cho bảo mật.
Nhóm đặc biệt dành thời gian để nghiên cứu cách tổ chức monorepo với Nx, giúp tối ưu hóa quy trình phát triển, CI. Nx giúp tự nhận biết project nào bị ảnh hưởng khi có thay đổi, từ đó chỉ build/test những phần cần thiết, tiết kiệm thời gian đáng kể.
-->

---
hideInToc: true
---

## Key Strengths

<CardRow :items="[
  {
    title: 'Speed & Scalability',
    content: 'Blazing fast graph processing and efficient communication via gRPC and Traefik Gateway',
    icon: 'i-carbon-flash'
  },
  {
    title: 'Optimized DevOps',
    content: 'Advanced CI/CD with custom GitHub Actions cache, reducing build times from 25m to 30s',
    icon: 'i-carbon-timer'
  },
  {
    title: 'Maintainability',
    content: 'Clean Architecture, DDD, and CQRS patterns ensuring a scalable and testable codebase',
    icon: 'i-carbon-security'
  }
]" />

<!--
Hệ thống có ưu điểm vượt trội về hiệu năng nhờ vào ngôn ngữ Go xử lý biểu đồ rất nhanh.
Quy trình DevOps được tối ưu hóa cực tốt với Nx và giải pháp cache tự xây dựng, giúp giảm thời gian build từ 25 phút xuống còn 30 giây trong trường hợp tối ưu.
Ngoài ra việc setup editor để làm việc trong monorepo cũng phức tạp. Chúng em đã phải tìm hiểu về language server protocol, cách cấu hình vì một số language server hỗ trợ monorepo, cần tinh chỉnh. Cài đặt `inotify-tools` giúp editor mở lên nhanh đáng kể, từ đơ 8s xuống không còn nhận thấy độ trễ nữa.
Mã nguồn cũng rất dễ bảo trì nhờ áp dụng các pattern như Clean Architecture và CQRS. Sử dụng SQL thuần, cùng SQL giúp linh hoạt hơn so với ORM.
-->

---
hideInToc: true
---

## Challenges Overcome

<CardRow :items="[
  {
    title: 'Learning Curve',
    content: 'Mastering complex distributed systems, Event-Driven patterns, and advanced RBAC models',
    icon: 'i-carbon-education'
  },
  {
    title: 'Resource Overhead',
    content: 'Optimizing infrastructure for enterprise-ready tools like Authentik and Redpanda',
    icon: 'i-carbon-meter'
  },
  {
    title: 'Integration Hurdles',
    content: 'Customizing BlockNote and parsing complex data from external sources like Obsidian',
    icon: 'i-carbon-settings-adjust'
  }
]" />

<!--
Nhóm đã phải vượt qua rào cản về công nghệ rất lớn khi học và áp dụng Microservices, Event-Driven, các thư viện Editor và Casbin cùng lúc.
Việc tối ưu hóa tài nguyên cho các công cụ Enterprise-ready cũng là một thách thức lớn. Như Authentik có thể sử dụng lên đến 1.5GB RAM trong quá trình phát triển ở máy.
Ngoài ra, việc tích hợp và tùy biến các thư viện như BlockNote hay xử lý dữ liệu từ Obsidian cũng tốn nhiều công sức, tuy nhiên cũng không được đúng chính xác vì quá trình transform chỉ parse bằng text, không phải bằng cây ngôn ngữ.
-->

---
hideInToc: true
---

## What Need to be Improved

<CardRow :items="[
  {
    title: 'UI/UX Polish',
    content: 'Refining the interface and user experience to ensure a smoother, more intuitive workflow',
    icon: 'i-carbon-user-favorite'
  },
  {
    title: 'Production Readiness',
    content: 'Standardizing health checks across all services and implementing final production-grade optimizations',
    icon: 'i-carbon-deploy'
  },
]" />

<!--
Trải nghiệm UI UX chưa được tối ưu, vẫn còn nhiều điểm chưa thân thiện với người dùng.
Chưa hoàn toàn thiết lập production ready, như health check endpoint chỉ có ở các service go, chưa có ở NestJS hay NextJS web.
-->

---
hideInToc: true
---

## Future Directions

<CardRow :items="[
  {
    title: 'Features Expansion, UI/UX Improvements',
    content: 'Implementing AI-powered editing and hybrid search for intelligent knowledge management. Enhancing UI/UX for better user experience',
    icon: 'i-carbon-bot'
  },
  {
    title: 'Cloud Native',
    content: 'Migrating to Istio Service Mesh on Kubernetes for enhanced security and traffic control',
    icon: 'i-carbon-kubernetes'
  },
  {
    title: 'Commercialization',
    content: 'Implementing subscription models and SaaS features to transform into a viable product',
    icon: 'i-carbon-shopping-cart'
  }
]" />

<!--
Trong tương lai, nhóm dự kiến sẽ tối ưu và mở rộng tính năng (publish, unpublish a note/workspace), cải thiện UI/UX,
cũng như tích hợp thêm AI vào editor để hỗ trợ người dùng tốt hơn.

Refactor kiến trúc frontend

Về hạ tầng, hệ thống sẽ được chuyển dịch sang Kubernetes với Istio Gateway để tận dụng các tính năng Service Mesh.

Thực hiện các tính năng thương mại hóa như mô hình subscription để tự động commit document,
vì quá trình này tốn nhiều tài nguyên để sync qua Search Service, cũng như các tính năng khác.
-->
