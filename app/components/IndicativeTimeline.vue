<template>
  <div class="rounded-lg border border-gray-200 bg-white/60 p-4 shadow-sm dark:border-gray-700 dark:bg-gray-900/40">
    <div class="flex flex-col gap-3">
      <div>
        <p class="text-sm font-semibold text-gray-800 dark:text-gray-100">Indicative timeline</p>
        <p class="text-xs text-gray-500 dark:text-gray-400">Scroll horizontally to explore all tenses at a glance.</p>
      </div>
      <div class="relative overflow-hidden">
        <div class="absolute inset-x-0 top-5 h-px bg-gray-200 dark:bg-gray-700"></div>
        <div class="flex gap-4 overflow-x-auto pb-2">
          <TimelineCard
            v-for="item in items"
            :key="item.key"
            :item="item"
            :format-label="formatLabel"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import TimelineCard from './TimelineCard.vue';

type TimelineItem = {
  key: string;
  label: string;
  sections: Array<{
    key: string;
    forms: Array<{ label: string; value: string }>;
  }>;
};

defineProps<{
  items: TimelineItem[];
  formatLabel: (label: string) => string;
}>();
</script>
