<template>
  <div id="todo-input-wrap">
    <input
      id="todo-input"
      type="text"
      v-model="newTodoItem"
      @keyup.enter="addTodo"
      placeholder="일단 할 일을 입력하세요!"
    />
    <span id="plus-btn" class="addContainer" @click="addTodo">
      <i class="far fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    // addTodo() {
    //   localStorage.setItem(this.newTodoItem, this.newTodoItem);
    //   this.clearInput();
    // },
    addTodo() {
      if (this.newTodoItem !== "") {
        let obj = { completed: false, item: this.newTodoItem };
        console.log(this.newTodoItem);
        localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
        let value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit("addTodo", value);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
};
</script>
<style>
#todo-input-wrap {
  text-align: center;
}
#todo-input {
  border: none;
  width: 40%;
  height: 40px;
  border-radius: 5px;
  font-size: 1rem;
  box-shadow: rgba(17, 12, 46, 0.15) 0px 48px 100px 0px;
  color: rgb(128, 144, 163);
  font-weight: bold;
}
#todo-input:focus {
  outline: none;
}
input::placeholder {
  color: rgb(128, 144, 163);
}
input::-webkit-input-placeholder {
  color: rgb(128, 144, 163);
}
input:-ms-input-placeholder {
  color: rgb(128, 144, 163);
}

#plus-btn {
  display: inline-block;
  background-color: rgb(128, 144, 163);
  padding: 0.7rem;
  margin-left: 10px;
  border-radius: 5px;
  box-shadow: rgba(17, 12, 46, 0.15) 0px 48px 100px 0px;
}
#plus-btn i {
  color: white;
}
</style>
