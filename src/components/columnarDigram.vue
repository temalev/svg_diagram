<template>
  <div class="main">
    <svg
      class="svg"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xhtml="http://www.w3.org/1999/xhtml"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      version="1.1"
      width="100%"
      height="100%"
      style="background-color: white; border: solid 1px black"
    >
      <rect
        v-for="(column, id) in newArr"
        :key="id"
        :width="`${100 / newArr.length}%`"
        :height="`${column}%`"
        :x="`${id * (100 / newArr.length)}%`"
        :y="`${100 - column}%`"
        @click="position"
        rx="1"
      />
    </svg>
    {{ newArr }}
  </div>
</template>
<script>
export default {
  name: "columnarDiagram",
  data() {
    return {
      columns: [
        { value: 100 },
        { value: 200 },
        { value: 230 },
        { value: 120 },
        { value: 111 },
        { value: 100 },
        { value: 200 },
        { value: 230 },
        { value: 400 },
        { value: 800 },
        { value: 930 },
        { value: 1000 },
        { value: 200 },
        { value: 630 },
        { value: 800 },
        { value: 600 },
        { value: 530 },
      ],
      newColumns: [],
    };
  },
  computed: {
    newArr() {
      const data = this.columns.map((el) => el.value);
      console.log(data);
      const max = Math.max(...data);
      const min = Math.min(...data);
      const newData = data.map((el) => 1 + 95 * ((el - min) / (max - min)));
      return newData;
    },
  },
  methods: {
    position(event) {
      console.log(event.y);
    },
  },
};
</script>
<style scoped>
.main {
  width: 100%;
  height: 500px;
}
.svg {
  overflow-x: scroll;
}
rect {
  fill: #1d7218;
}
rect:hover {
  fill: #0d243c;
  cursor: pointer;
}
</style>
