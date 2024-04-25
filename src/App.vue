<template>
  <div class="container">
    <div class="lists">
      <ul>
        <li v-for="list in lists" v-bind:key="list">
          <label class="item">
            <input v-on:click="addBlocks" type="checkbox" v-model="checked" />
            <h2>List {{ list }}</h2>
            <select></select>
          </label>
        </li>
      </ul>
    </div>
    <div class="blocks">
      <h2>List 1</h2>
      <ul class="blocksLine">
        <li v-for="block in blocks" v-bind:key="block">
          <div class="block"></div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import {
  countRedItem,
  /*   countYellowItem,
  countGreenItem,
  countBlueItem, */
} from "./constants";

export default {
  data() {
    return {
      lists: 5,
      blocks: 0,
      checked: false,
    };
  },
  methods: {
    addBlocks() {
      if (!this.checked) {
        this.blocks += countRedItem;
      } else {
        this.blocks -= countRedItem;
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 50% 50%;
  width: 80%;
  margin: 0 10%;
  border: 1px solid black;
}
.blocks {
  border: 1px solid black;
  margin: 20px;
}
.lists {
  border: 1px solid black;
  margin: 20px;
}
.blocks li {
  list-style-type: none;
}
.block {
  width: 20px;
  height: 20px;
  background-color: red;
  margin: 2px;
  border: 1px solid black;
}
.blocksLine {
  display: flex;
  padding-left: 0;
}
.lists li {
  list-style-type: none;
}
.item {
  display: inline-flex;
  gap: 10px;
}
</style>
