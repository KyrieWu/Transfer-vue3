<template>
  <h1 class="list-title">{{ title }}</h1>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    default: "列表",
  },
});
</script>

<style lang="scss" scoped>
.list-title {
  height: 38px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: normal;
  margin: 0;
  color: #666;
  font-size: 14px;
  border-bottom: 1px solid #ddd;
  background-color: #efefef;
}
</style>
