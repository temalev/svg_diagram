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
      <g
        :style="{
          transform: `translateX(${id * (100 / columns.length)}%)`,
        }"
        v-for="(column, id) in columns"
        :key="id"
        class="block"
      >
        <rect
          v-for="(col, idCol) in column"
          :key="col.val"
          :width="`${40 / columns.length}%`"
          :height="`${1 + 95 * ((col.val - min) / (max - min))}%`"
          :x="`${idCol * (42 / columns.length)}%`"
          :y="`${100 - (1 + 95 * ((col.val - min) / (max - min)))}%`"
          rx="1"
        />
      </g>
    </svg>
  </div>
</template>
<script>
export default {
  name: "columnarDiagram",
  data() {
    return {
      columns: [
        [{ val: 400 }, { val: 390 }],
        [{ val: 700 }, { val: 590 }],
        [{ val: 300 }, { val: 890 }],
        [{ val: 400 }, { val: 390 }],
        [{ val: 700 }, { val: 590 }],
        [{ val: 300 }, { val: 1890 }],
        [{ val: 700 }, { val: 590 }],
        [{ val: 300 }, { val: 890 }],
        [{ val: 400 }, { val: 390 }],
        [{ val: 700 }, { val: 590 }],
        [{ val: 300 }, { val: 890 }],
        [{ val: 400 }, { val: 390 }],
      ],
      newColumns: [],
    };
  },
  computed: {
    min() {
      return Math.min(
        ...this.columns.reduce(
          (acc, col) => [...acc, Math.min(...col.map(({ val }) => val))],
          []
        )
      );
    },
    max() {
      return Math.max(
        ...this.columns.reduce(
          (acc, col) => [...acc, Math.max(...col.map(({ val }) => val))],
          []
        )
      );
    },
    // newArr() {
    //   const data = this.columns.map((el) => el.val);
    //   console.log(data);
    //   const max = this.columns.reduce(
    //     (acc, col) => [...acc, Math.max(...col.map(({ val }) => val))],
    //     []
    //   );
    //   const min = this.columns.reduce(
    //     (acc, col) => [...acc, Math.min(...col.map(({ val }) => val))],
    //     []
    //   );
    //   const newData = data.map((el) => 1 + 95 * ((el - min) / (max - min)));
    //   return newData;
    // },
  },
  methods: {
    position(options) {
      console.log(options);
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
.block {
  background-color: #0d243ca4;
}
rect {
  fill: #1d7218;
}
rect:hover {
  fill: #0d243c;
  cursor: pointer;
}
</style>
