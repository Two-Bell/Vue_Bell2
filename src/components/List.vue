<template>
  <div class="listContainer">
    <div class="list" v-for="(data, index) in list" :key="index">
      <div>key : {{ data.key }}</div>
      <div>title : {{ data.title }}</div>
      <div>content : {{ data.content }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
interface Item {
  key: number;
  title: string;
  content: string;
}
@Component
export default class List extends Vue {
  // @Prop() public list: { type: Item[]; default: [] };
  @Prop({ default: [], required: true })
  list!: Item[];
}
</script>

<style scoped>
.listContainer {
  border-top: 1px solid palevioletred;
  border-bottom: 1px solid palevioletred;
}
.list {
  display: flex;
}
.list > div {
  padding: 5px;
}
</style>
