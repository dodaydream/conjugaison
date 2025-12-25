<template>
<UTimeline
  :items="items"
  orientation="horizontal"
  :ui="{ item: 'odd:flex-col-reverse odd:-translate-y-[calc(100%-1rem)]', root: 'w-full' }"
  class="h-full"
  size="2xs"
  :default-value="5"
>
  <template #description="{item}">
    <div>
      <TimelineCard :item="item" :format-label="formatLabel"/>
    </div>
  </template>
</UTimeline>
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
