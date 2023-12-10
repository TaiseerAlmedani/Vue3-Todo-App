<script>
export default {
  props: {
    initalTags: Array,
    currentTag: String,
  },
  computed: {
    tags() {
      return ["all", ...new Set(this.initalTags)];
    },
  },
}
</script>
<template>
  <button :class="{ 'active': currentTag === tag }" @click="$emit('update:currentTag', tag)" v-for="tag in tags">
    {{ tag }}
  </button>
</template>