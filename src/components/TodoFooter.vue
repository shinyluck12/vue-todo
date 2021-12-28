<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" @click="clearTodo">Delete All</span>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    clearTodo() {
      this.$emit("removeAll");
    },
  },
};
</script>
<style>
.clearAllContainer {
  width: 10%;
  height: 40px;
  background-color: rgb(81, 79, 161);
  color: #fff;
  margin: auto;
  border-radius: 5px;
  position: relative;
}
.clearAllContainer span {
  /* height: 100%; */
  width: 100%;
  display: inline-block;
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  font-size: 1rem;
  font-weight: 600;
  text-align: center;
}
</style>
