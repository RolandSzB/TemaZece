<template>
  <div class="app-container">
    <div class="cell-rows">
      <div class="cell-row" v-for="rowIndex in 2" :key="rowIndex">
        <Cells
          v-for="cellIndex in 6"
          :key="cellIndex"
          :initialColor="generateRandomColor"
          ref="cells"
        />
      </div>
    </div>
    <button @click="regenerateColors">Regenerate Colors</button>
  </div>
</template>

<script>
import Cells from "./components/Cells.vue";

export default {
  components: {
    Cells,
  },
  methods: {
    regenerateColors() {
      this.$refs.cells.forEach((cell) => {
        cell.cellColor = this.generateRandomColor();
      });
    },
    generateRandomColor() {
      const letters = "0123456789ABCDEF";
      let color = "#";
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    },
  },
};
</script>

<style>
.app-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 30rem;
}

.cell-rows {
  display: flex;
  flex-direction: column;
}

.cell-row {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 10rem;
  width: 80rem;
}

button {
  margin-top: 2rem;
  padding: 1rem 2rem;
  background-color: gray;
  color: black;
  border-radius: 1rem;
  cursor: pointer;
}
</style>
