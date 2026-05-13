<script setup lang="ts">
interface CardItem {
  title: string
  content: string
  icon?: string
}

defineProps<{
  items: CardItem[]
}>()
</script>

<template>
  <div class="flex flex-row flex-wrap gap-4 w-full justify-center my-4">
    <div 
      v-for="(item, index) in items" 
      :key="index"
      class="flex-1 min-w-[250px] max-w-[400px] slidev-card p-5"
    >
      <div v-if="item.icon" :class="[item.icon, 'text-3xl mb-3 text-primary opacity-80']" />
      <h3 class="text-xl slidev-card-title mb-2">
        {{ item.title }}
      </h3>
      <p class="text-sm slidev-card-text leading-relaxed">
        {{ item.content }}
      </p>
    </div>
  </div>
</template>

