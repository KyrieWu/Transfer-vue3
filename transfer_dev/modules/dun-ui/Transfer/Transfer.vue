<template>
  <div>
    <div>
      <select @change="setTargetIndex($event.target.value)">
        <option v-for="(title, index) of options" :key="index" :value="index">
          {{ title }}
        </option>
      </select>
    </div>
    <div class="transfer">
      <div class="box left-list">
        <h1 class="left-title">{{ leftTitle }}</h1>
      </div>
      <div class="box button-group"></div>
      <div class="box right-list"></div>
    </div>
  </div>
</template>

<script setup>
import propsDefination from "./extends/props";
import { useTargetIndex, useComputedData } from "./extends/hooks";

const props = defineProps(propsDefination);
const options = props.data.map(({ title }) => title);

const [targetIndex, setTargetIndex] = useTargetIndex(0);

console.log(props.data);
const { leftTitle } = useComputedData(props.data, targetIndex);
</script>

<style></style>
