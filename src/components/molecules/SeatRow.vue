<template>
  <ul
    id="seat-list"
    class="seat-row"
    role="listitem"
    :aria-activedescendant="activeId"
  >
    <li></li>
    <Seat v-for="s in row" :key="s.id" :seat="s" v-model="selected" />
  </ul>
</template>

<script setup lang="ts">
import Seat, { type SeatData } from '../atoms/Seat.vue';
import { computed } from 'vue';

const props = defineProps<{
  row: SeatData[];
  modelValue: string;
  activeId: string;
}>();

const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void;
}>();

const selected = computed({
  get: () => props.modelValue,
  set: (value: string) => emit('update:modelValue', value),
});
</script>

<style>
.seat-row {
  display: flex;
  gap: 8px;
  margin-bottom: 12px;
}
</style>
