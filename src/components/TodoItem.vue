<template>
   <div class="item" :class="{done: todoItem.completed}">
    <label>
      <input type="checkbox" :checked="todoItem.completed" @click="$emit('change-state', $event)">
      {{todoItem.content}}
      <span class="checkbtn"></span>
    </label>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoItem"]
}
</script>

<style>
.item {
  padding: 16px;
  border-radius: 8px;
  background-color: #fff;
  color: #666;
}

.item.done label {
  color: #ccc;
  text-decoration: line-through;
  font-style: italic;
}

.item label {
  position: relative;
  display: flex;
  align-items: center;
}

.item label span.checkbtn {
  position: absolute;
  top: 2px;
  cursor: pointer;
}

.item label span.checkbtn::before, 
.item label span.checkbtn::after {
  content: "";
  display: block;
  position: absolute;
  width: 18px;
  height: 18px;
  border-radius: 50%;
}

.item label span.checkbtn::before {border: 1px solid hsl(210, 80%, 50%);}

.item label span.checkbtn::after {
  transition: all .4s;
  background-color: hsl(210, 80%, 50%);
  transform: translate(1px, 1px) scale(.8);
  opacity: 0;
}

.item input {
  margin-right: 16px;
  opacity: 0;
}

.item input:checked + span.checkbtn::after {opacity: 1;}
</style>
