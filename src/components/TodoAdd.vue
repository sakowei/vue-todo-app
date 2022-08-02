<template>
  <div class="add">
    <input type="text" name="todo" v-model="todoContent" @keyup.enter="emitAdd">
    <button @click="emitAdd">
      <i class="plus"></i>
    </button>
  </div>
</template>

<script>
import {ref} from "vue";

export default {
  name: "TodoAdd",
  setup(pros, context) {
    const todoContent = ref("");
    const emitAdd = () => {
      const todo = {
        id: pros.tid,
        content: todoContent.value,
        completed: false
      };
      context.emit("add-todo", todo);
      todoContent.value = "";
    };

    return {
      todoContent,
      emitAdd
    };
  }
}
</script>

<style>
.add {
  position: relative;
  display: flex;
  align-items: center;
}

.add input {
  padding: 16px 52px 16px 18px;
  width: 100%;
  border: none;
  border-radius: 48px;
  font-size: 16px;
  color: #666;
  outline: none;
  box-shadow: 0 0 24px rgba(0, 0, 0, .08);

}

.add button {
  position: absolute;
  right: 2px;
  width: 46px;
  height: 46px;
  border-radius: 50%;
  border: none;
  color: #fff;
  background-image:linear-gradient(hsl(210, 80%, 50%), hsl(180, 80%, 50%));
  outline: none;
  cursor: pointer;
}

.add button .plus {
  display: block;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(#fff,#fff), linear-gradient(#fff, #fff);
  background-size: 50% 2px, 2px 50%;
  background-position: center;
  background-repeat: no-repeat;
}
</style>
