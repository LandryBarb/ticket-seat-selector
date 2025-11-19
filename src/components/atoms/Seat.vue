<template>
  <div
    class="seat"
    :class="{
      selected: modelValue === seat.id,
      occupied: seat.occupied,
    }"
    @click="select"
  >
    {{ seat.label }}
  </div>
</template>

<script setup lang="ts">
export interface SeatData {
  id: string;
  label: string;
  occupied: boolean;
}

const props = defineProps<{
  seat: SeatData;
  modelValue: string;
}>();

const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void;
}>();

function select() {
  if (!props.seat.occupied) {
    emit('update:modelValue', props.seat.id);
  }
}
</script>

<style>
.seat {
  width: 40px;
  height: 40px;
  border: 1px solid #aaa;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.selected {
  background: #4caf50;
  color: #fff;
}

.occupied {
  background: #ccc;
  cursor: not-allowed;
}
</style>
