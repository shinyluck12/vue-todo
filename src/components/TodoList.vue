<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" :key="todoItem">
        <i
          class="checkBtn fas fa-check"
          :class="{ checkBtnCompleted: todoItem.completed }"
          @click="toggleComplete(todoItem, index)"
        >
          <span
            class="todo-cont"
            :class="{ textCompleted: todoItem.completed }"
            >{{ todoItem }}</span
          >
        </i>
        <span class="removeBtn" @click="removeTodo(todoItem, index)">
          <i class="fas fa-eraser"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo(todoItem, index) {
      // localStorage.removeItem(todoItem);
      // this.todoItems.splice(index, 1);
      this.$emit("removeItem", todoItem, index);
    },
    toggleComplete(todoItem, index) {
      // localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
      // todoItem.completed = !todoItem.completed;
      // localStorage.removeItem(todoItem.item);
      this.$emit("toggleItem", todoItem, index);
    },
  },
  // created() {
  //   if (localStorage.length > 0) {
  //     for (let i = 0; i < localStorage.length; i++) {
  //       if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
  //         console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
  //         this.todoItems.push(
  //           JSON.parse(localStorage.getItem(localStorage.key(i)))
  //         );
  //       }
  //     }
  //   }
  // },
};
</script>

<style>
ul {
  width: 100%;
  padding: 0;
  margin-bottom: 60px;
}
li {
  list-style: none;
  width: 41%;
  height: 20px;
  background-color: white;
  margin: auto;
  border-radius: 5px;
  /* margin-top: 10px; */
  border-bottom: 1px solid lightgray;
  padding: 0.5rem;
}
.checkBtn {
  color: rgb(128, 144, 163);
  vertical-align: middle;
}
.todo-cont {
  margin-left: 10px;
}
.removeBtn {
  color: rgb(255, 35, 86);
  float: right;
}
.removeBtn i {
  vertical-align: middle;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
</style>
