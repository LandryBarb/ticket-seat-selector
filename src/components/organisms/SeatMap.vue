<template>
  <div class="seat-map">
    <SeatRow
      v-for="(row, i) in seats"
      :key="i"
      :row="row"
      v-model="selectedSeat"
    />

    <div class="info">
      <strong>Selected Seat:</strong>
      {{ selectedSeat || 'None' }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import SeatRow from '../molecules/SeatRow.vue';
import type { SeatData } from '../atoms/Seat.vue';

// Mock data w/ strong typing
const seats = ref<SeatData[][]>([
  [
    { id: 'A1', label: 'A1', occupied: false },
    { id: 'A2', label: 'A2', occupied: true },
    { id: 'A3', label: 'A3', occupied: false },
    { id: 'A4', label: 'A4', occupied: false },
    { id: 'A5', label: 'A5', occupied: false },
  ],
  [
    { id: 'B1', label: 'B1', occupied: false },
    { id: 'B2', label: 'B2', occupied: false },
    { id: 'B3', label: 'B3', occupied: true },
    { id: 'B4', label: 'B4', occupied: false },
    { id: 'B5', label: 'B5', occupied: false },
  ],
  [
    { id: 'C1', label: 'C1', occupied: false },
    { id: 'C2', label: 'C2', occupied: false },
    { id: 'C3', label: 'C3', occupied: false },
    { id: 'C4', label: 'C4', occupied: true },
    { id: 'C5', label: 'C5', occupied: false },
  ],
]);

const selectedSeat = ref<string>('');
</script>

<style>
.seat-map {
  margin-top: 2rem;
}

.info {
  margin-top: 1rem;
  font-size: 1.2rem;
}
</style>
