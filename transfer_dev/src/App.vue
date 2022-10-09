<script setup>
import { Transfer } from "../modules/dun-ui";

const data = [
  {
    title: "华为",
    data: [
      {
        id: 1,
        phone_name: "Mate 40 pro",
        disabled: false,
      },
      {
        id: 2,
        phone_name: "Mate 30 pro",
        disabled: true,
      },
      {
        id: 3,
        phone_name: "Mate 50 pro",
        disabled: false,
      },
      {
        id: 4,
        phone_name: "P 40 pro",
        disabled: false,
      },
    ],
  },
  {
    title: "苹果",
    data: [
      {
        id: 5,
        phone_name: "iphone 12 pro",
        disabled: false,
      },
      {
        id: 6,
        phone_name: "iphone 11 pro",
        disabled: false,
      },
      {
        id: 7,
        phone_name: "iphone 13 pro",
        disabled: true,
      },
      {
        id: 8,
        phone_name: "iphone 14 pro",
        disabled: false,
      },
    ],
  },
  {
    title: "小米",
    data: [
      {
        id: 5,
        phone_name: "xiaomi 12 pro",
        disabled: false,
      },
      {
        id: 6,
        phone_name: "xiaomi 11 pro",
        disabled: true,
      },
      {
        id: 7,
        phone_name: "xiaomi 13 pro",
        disabled: false,
      },
      {
        id: 8,
        phone_name: "xiaomi 10 pro",
        disabled: true,
      },
    ],
  },
];
</script>

<template>
  <div>
    <transfer :data="data" right-title="已选择机型"></transfer>
  </div>
</template>

<style scoped></style>
