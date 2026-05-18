<script setup>
import { ref, computed } from 'vue'

const logos = [
  { name: 'Go', src: '/go-logo.svg' },
  { name: 'TypeScript', src: '/typescript-logo.svg' },
  { name: 'PostgreSQL', src: '/postgres-logo.svg' },

  { name: 'Yjs', src: '/yjs-logo.svg' },
  { name: 'ProseMirror', src: '/prosemirror-logo.svg' },
  { name: 'Tiptap / Hocuspocus', src: '/tiptap-logo.svg' },
  { name: 'Blocknote', src: '/blocknote-logo.svg' },

  { name: 'Watermill', src: '/watermill-logo.svg' },
  { name: 'Casbin', src: '/casbin-logo.svg' },
  { name: 'NestJS', src: '/nestjs-logo.svg' },

  { name: 'React', src: '/react-logo.svg' },
  { name: 'Tailwind CSS', src: '/tailwindcss-logo.svg' },
  { name: 'Shadcn UI', src: '/shadcnui-logo.svg' },
  { name: 'Redux', src: '/redux-logo.svg' },
  { name: 'Next.js', src: '/nextjs-logo.svg' },

  { name: 'Redocly', src: '/redocly-logo.svg' },
  { name: 'OpenAPI', src: '/openapi-logo.svg' },
  { name: 'Scalar', src: '/scalar-logo.svg' },
  { name: 'gRPC', src: '/grpc-logo.svg' },

  { name: 'Traefik', src: '/traefik-logo.svg' },
  { name: 'Authentik', src: '/authentik-logo.svg' },
  { name: 'Meilisearch', src: '/meilisearch-logo.svg' },
  { name: 'Redpanda', src: '/redpanda-logo.svg' },
  { name: 'RustFS', src: '/rustfs-logo.svg' },
  { name: 'Nx', src: '/nx-logo.svg' },
  { name: 'Oxc', src: '/oxc-logo.svg' },
  { name: 'Rspack', src: '/rspack-logo.svg' },

  { name: 'OpenTelemetry', src: '/opentelemetry-logo.svg' },
  { name: 'Prometheus', src: '/prometheus-logo.svg' },
  { name: 'Grafana Loki', src: '/grafana-loki-logo.svg' },
  { name: 'Grafana Tempo', src: '/grafana-tempo-logo.svg' },
  { name: 'Grafana Alloy', src: '/grafana-alloy-logo.svg' },
  { name: 'Grafana', src: '/grafana-logo.svg' },
]

const itemsPerPage = 12
const currentPage = ref(0)
const totalPages = Math.ceil(logos.length / itemsPerPage)

const visibleLogos = computed(() => {
  const start = currentPage.value * itemsPerPage
  return logos.slice(start, start + itemsPerPage)
})

function nextPage() {
  currentPage.value = (currentPage.value + 1) % totalPages
}
function prevPage() {
  currentPage.value = (currentPage.value - 1 + totalPages) % totalPages
}
</script>

<template>
  <div class="relative w-full">
    <!-- Grid Container -->
    <div class="grid grid-cols-4 gap-4 p-2 min-h-[260px]">
      <div 
        v-for="logo in visibleLogos" 
        :key="logo.name"
        class="flex flex-col items-center justify-center p-3 slidev-card"
      >
        <div class="w-12 h-12 flex items-center justify-center mb-2">
          <img :src="logo.src" :alt="logo.name" class="w-full h-full object-contain" />
        </div>
        <span class="text-xs font-medium slidev-card-text text-center line-clamp-1">
          {{ logo.name }}
        </span>
      </div>
    </div>

    <!-- Controls -->
    <div class="flex items-center justify-center gap-4 mt-4 text-xs">
      <button @click="prevPage" class="slidev-btn">← Prev</button>
      <span class="text-gray-500">{{ currentPage + 1 }} / {{ totalPages }}</span>
      <button @click="nextPage" class="slidev-btn">Next →</button>
    </div>
  </div>
</template>
