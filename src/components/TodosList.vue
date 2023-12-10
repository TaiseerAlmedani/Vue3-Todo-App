<script>
import TodosItem from './TodosItem.vue';
import TodosTags from './TodosTags.vue';
export default {
  components: {
    TodosItem,
    TodosTags
  },
  props: {
    title: String,
    todosArray: Array,
    className: String,
  },
  data() {
    return {
      currentTag: "all",
    };
  },
  computed: {
    filteredArray() {
      if (this.currentTag === "all") return this.todosArray;
      return this.todosArray.filter((a) => a.tag === this.currentTag);
    },
  },
}
</script>
<template>
  <div :class="className" v-if="todosArray.length">
    <h1>{{ title }} ({{ todosArray.length }})</h1>
    <todos-tags v-model:currentTag="currentTag" :initalTags="todosArray.map(a => a.tag)"></todos-tags>
    <ul>
      <transition-group>
        <todos-item v-for="todo in filteredArray" :key="todo.id" :todoItem="todo">
        </todos-item>
      </transition-group>
    </ul>
  </div>
</template>