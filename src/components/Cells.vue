<template>
  <div :style="{ backgroundColor: cellColor }" class="cell">
    <p>{{ cellColor }}</p>
  </div>
</template>

<script>
export default {
  props: {
    initialColor: String,
  },
  data() {
    return {
      cellColor: this.initialColor,
    };
  },
  watch: {
    initialColor(newColor) {
      this.cellColor = newColor;
    },
  },
};
</script>

<style scoped>
.cell {
  width: 20%;
  padding-bottom: 10%;
  margin: 1%;
  text-align: center;
}

p {
  margin: 0;
  color: white;
}
</style>
