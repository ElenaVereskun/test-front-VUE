<template>
  <input value="" name="" id="" type="checkbox" v-model="post.categories" />
  List 1
  <label for="id">{{ label }}</label>
</template>

<script>
const props = defineProps({
  name: {
    type: String,
    default: "",
  },
  id: {
    type: String,
    default: "",
  },
  value: {
    type: String,
    default: "",
  },
  label: {
    type: String,
    default: "",
  },
});
export default {};
</script>

<style scoped></style>
