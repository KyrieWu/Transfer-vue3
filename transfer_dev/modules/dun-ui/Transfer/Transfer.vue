<template>
  <div>
    <div>
      <Selector :data="options" @select-change="setTargetIndex"></Selector>
    </div>
    <div class="transfer">
      <div
        class="box left-list"
        @dragover.prevent
        @dragend="addRightListData([dragedItem])"
      >
        <ListTItle :title="leftTitle"></ListTItle>
        <div>
          <listitem
            :data="leftListData"
            left-or-right="left"
            @checkbox-click="setCheckedData"
            @drag-item="setDregedItem"
          ></listitem>
        </div>
      </div>
      <ButtonGroup
        :left-button-disabled="transferButtonDisabled.left"
        :right-button-disabled="transferButtonDisabled.right"
        @left-button-click="removeRightListData(checkedData.right)"
        @right-button-click="addRightListData(checkedData.left)"
      ></ButtonGroup>
      <div
        class="box right-list"
        @dragover.prevent
        @dragend="removeRightListData([dragedItem])"
      >
        <ListTItle :title="rightTitle"></ListTItle>
        <div>
          <listitem
            :data="rightListData"
            left-or-right="right"
            @checkbox-click="setCheckedData"
            @drag-item="setDregedItem"
          ></listitem>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import Selector from "./components/Selector.vue";
import ListTItle from "./components/ListTItle.vue";
import ButtonGroup from "./components/ButtonGroup";
import Listitem from "./components/Listitem";

import propsDefination from "./extends/props";
import {
  useTargetIndex,
  useComputedData,
  useRightListData,
  useCheckedData,
  useDragedItem,
} from "./extends/hooks";

const props = defineProps(propsDefination);
const options = props.data.map(({ title }) => title);

const [targetIndex, setTargetIndex] = useTargetIndex(0);

const [checkedData, addCheckedData, removeCheakedData] = useCheckedData();

const [rightListData, addRightListData, removeRightListData] = useRightListData(
  [],
  checkedData
);

const [dragedItem, setDregedItem] = useDragedItem();

const { leftTitle, leftListData, transferButtonDisabled } = useComputedData(
  props.data,
  targetIndex,
  rightListData,
  checkedData
);

const setCheckedData = (checked, leftOrRight, item) => {
  checked
    ? addCheckedData(leftOrRight, item)
    : removeCheakedData(leftOrRight, item.id);
};
</script>

<style lang="scss" scoped>
.transfer {
  display: flex;
  flex-direction: row;
  width: 360px;
  height: 360px;
  border: 1px solid #ddd;

  .box {
    width: 120px;
    height: 100%;

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
  }
}
</style>
