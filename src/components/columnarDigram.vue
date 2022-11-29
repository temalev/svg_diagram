<template>
  <div class="main">
    <svg
      class="svg"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xhtml="http://www.w3.org/1999/xhtml"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      version="1.1"
      width="900"
      height="600"
      viewBox="0 0 300 300"
      style="background-color: white; border: solid 1px black"
    >
      <rect
        v-for="(column, id) in columns"
        :key="id"
        width="20px"
        :height="`${column.value}px`"
        fill="#123456"
        :x="id * 22"
        :y="0"
        @click="position"
      />
    </svg>
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
        { value: 180 },
        { value: 300 },
        { value: 420 },
      ],
    };
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
  width: 900px;
  height: 600px;
}
.svg {
}
</style>
