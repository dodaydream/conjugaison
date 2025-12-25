<template>
  <div
    class="relative flex w-44 flex-none flex-col gap-2 rounded-lg border border-gray-200 bg-white p-3 text-left shadow-sm dark:border-gray-700 dark:bg-gray-900"
  >
    <div class="flex items-center gap-2">
      <span class="h-2.5 w-2.5 rounded-full bg-primary-500 ring-4 ring-primary-100 dark:ring-primary-950"></span>
      <p class="text-xs font-semibold uppercase tracking-wide text-gray-600 dark:text-gray-300">
        {{ item.label }}
      </p>
    </div>
    <div v-for="section in item.sections" :key="section.key" class="space-y-1">
      <p class="text-[0.7rem] font-semibold uppercase tracking-wide text-gray-500 dark:text-gray-400">
        {{ formatLabel(section.key) }}
      </p>
      <ul class="space-y-0.5 text-xs text-gray-700 dark:text-gray-200">
        <li
          v-for="form in section.forms"
          :key="form.label + form.value"
          class="grid grid-cols-[minmax(2.5rem,3.5rem)_1fr] gap-2"
        >
          <span v-if="form.label" class="font-medium text-gray-500 dark:text-gray-400">
            {{ form.label }}
          </span>
          <span>{{ form.value }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
type TimelineItem = {
  key: string;
  label: string;
  sections: Array<{
    key: string;
    forms: Array<{ label: string; value: string }>;
  }>;
};

defineProps<{
  item: TimelineItem;
  formatLabel: (label: string) => string;
}>();
</script>
