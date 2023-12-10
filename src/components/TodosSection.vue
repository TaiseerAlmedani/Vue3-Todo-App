<script>
import TodosAdd from "./TodosAdd.vue"
import TodosList from "./TodosList.vue"
export default {
  components: {
    TodosAdd,
    TodosList
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "study the vue lesson",
          isComplete: false,
          tag: "course",
        },
        { id: 2, title: "Do the homework", isComplete: false, tag: "course" },
        { id: 3, title: "Read from the Docs", isComplete: false, tag: "study" },
        { id: 4, title: "Make mony", isComplete: true, tag: "work" },
      ],
    };
  },
  computed: {
    InProgress() {
      return this.todos.filter((todoItem) => !todoItem.isComplete);
    },
    Done() {
      return this.todos.filter((todoItem) => todoItem.isComplete);
    },
  },
  methods: {
    add(addThisTitle, addThisTag) {
      this.todos.push({
        id: this.todos.length + 1,
        title: addThisTitle,
        isComplete: false,
        tag: addThisTag,
      });
    },
  },
}
</script>
<template>
  <h1 class="main-title">Vue3 Todo App</h1>
  <todos-add @addToTheArray="add"></todos-add>
  <Transition>
    <todos-list title="In Progress" className="inProgress" v-bind:todosArray="InProgress">
      this is slot
    </todos-list>
  </Transition>
  <Transition>
    <todos-list title="Done" className="done" v-bind:todosArray="Done">
    </todos-list>
  </Transition>
</template>