<template>
  <div class="todo">
    <h3>{{ info.title }}</h3>
    <div class="description">
      <p>{{ info.description }}</p>
      <input type="checkbox" :checked="info.complete" @click="handleClick" />
    </div>
  </div>
</template>

<script>
export default {
  name: "todo",
  props: ["info", "index"],
  methods: {
    handleClick() {
      this.$emit("set-complete", !this.info.complete, this.index);
    },
  },
};
</script>

<style lang="scss" scoped>
.todo {
  background: #f0f0f0;
  margin: 8px;
  padding: 8px;
  border: 1px solid #fff;
  border-radius: 12px;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.125),
    -4px -4px 12px rgba(255, 255, 255, 1);

  h3 {
    font-size: 20px;
    background: linear-gradient(90deg, #cb2d3e, #ef473a);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .description {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .complete {
    text-decoration: line-through;
  }
}
</style>
