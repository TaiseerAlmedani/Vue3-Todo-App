<script>
export default {
  props: {
    todoItem: Object,
  },
}
</script>
<template>
  <li>
    <label>
      {{ todoItem.id }}: {{ todoItem.title }}
      <input type="checkbox" v-model="todoItem.isComplete" />
    </label>
  </li>
</template>