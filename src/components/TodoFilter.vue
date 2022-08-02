<template>
  <div class="filters">
    <span
    v-for="filter in filters"
    :key="filter.value"
    @click="$emit('change-filter', filter.value)"
    class="filter"
    :class="{active: selected === filter.value}">{{filter.label}}</span>
  </div>
</template>

<script>
export default {
  props: ["selected"],
  name: "TodoFilter",
  setup() {
     const filters = [
      {label: "全部", value: "all"},
      {label: "已完成", value: "done"},
      {label: "未完成", value: "todo"},
    ];

    return {
      filters
    }
  }
}
</script>

<style>
  .filters {
    display: flex;
    margin: 24px 2px;
    color: #ccc;
    font-size: 14px;
  }

  .filters .filter {
    margin-right: 14px;
    transition: all .8s;
    cursor: pointer;
  }

  .filter.active {
    color: #6b7c9c;
    font-weight: 600;
    transform: scale(1.2);
  }
</style>
