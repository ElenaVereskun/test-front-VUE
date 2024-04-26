<template>
  <div class="container">
    <div class="lists">
      <ul>
        <li v-for="list in lists" v-bind:key="list" class="list">
          <!-- <img
            src="./image/arrow-right.svg"
            height="15px"
            @close="onClose"
            @open="onOpen"
          /> -->
          <input type="checkbox" v-model="selectAll" @change="toggleAllItems" />
          List {{ list }}
          <div v-for="item in items" :key="item.id" style="display: flex">
            <input
              type="checkbox"
              v-model="item.checked"
              @change="toggleItem(item)"
            />
            {{ item.id }} Item

            <div>
              <input type="number" class="inputNumber" value=" " />{{
                item.count
              }}
              <input type="color" class="inputColor" value="#1aff00" />
            </div>
          </div>

          <!--  <ul class="items">
              <li class="countBlock">
                <label class="list">
                  <input
                    v-on:click="addBlocks"
                    type="checkbox"
                    v-model="arr"
                    value="7"
                  />
                  <span> Item 1</span>
                </label>
                <div>
                  <input type="number" class="inputNumber" value="7" />
                  <input type="color" class="inputColor" value="#ff0000" />
                </div>
              </li>
              <li class="countBlock">
                <label class="list">
                  <input
                    v-on:click="addBlocks"
                    type="checkbox"
                    v-model="arr"
                    value="40"
                  />
                  <span> Item 2</span>
                </label>
                <div>
                  <input type="number" class="inputNumber" value="40" />
                  <input type="color" class="inputColor" value="#1aff00" />
                </div>
              </li>
              <li class="countBlock">
                <label class="list">
                  <input
                    v-on:click="addBlocks"
                    type="checkbox"
                    v-model="arr"
                    value="10"
                  />
                  <span> Item 3</span>
                </label>
                <div>
                  <input type="number" class="inputNumber" value="10" />
                  <input type="color" class="inputColor" value="#002bff" />
                </div>
              </li>
              <li class="countBlock">
                <label class="list">
                  <input
                    v-on:click="addBlocks"
                    type="checkbox"
                    v-model="arr"
                    value="5"
                  />
                  <span> Item 4</span>
                </label>
                <div>
                  <input type="number" class="inputNumber" value="5" />
                  <input type="color" class="inputColor" value="#ffdd00" />
                </div>
              </li>
            </ul> -->
        </li>
      </ul>
    </div>
    <div class="blocks">
      <div class="blocksList">
        <ul>
          <li v-for="list in lists" v-bind:key="list" class="list">
            <div class="blocksTop">
              <h3>List {{ list }}</h3>
              <button @click="sortsBlocks" class="btn">Перемешать</button>
            </div>

            <div class="containerBlocks">
              <div
                v-for="block in blocks"
                v-bind:key="block"
                class="blocksLine"
              >
                <div
                  v-on:click="deleteBlock"
                  class="block"
                  @change="selectedColor"
                  :style="{ backgroundColor: selectedColor }"
                ></div>
              </div>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
  <div></div>
</template>

<script>
export default {
  data() {
    return {
      lists: 5,
      blocks: 0,
      items: [
        { id: 1, color: "red", count: 10, checked: false },
        { id: 2, color: "yellow", count: 16, checked: false },
        { id: 3, color: "green", count: 40, checked: false },
        { id: 4, color: "blue", count: 0, checked: false },
      ],
      selectAll: false,
    };
  },
  computed: {
    selectedItemsCount() {
      return this.items
        .filter((item) => item.checked)
        .reduce((total, item) => total + item.count);
    },
    selectedColor() {
      return this.items.find((item) => item.checked)?.color || "transparent";
    },
  },

  methods: {
    deleteBlock() {
      this.blocks -= 1;
    },
    toggleItem(item) {
      if (item.checked) {
        this.blocks += item.count;
      } else {
        this.blocks -= item.count;
      }
    },
    toggleAllItems() {
      if (this.selectAll) {
        this.items.forEach((item) => (item.checked = true));
      } else {
        this.items.forEach((item) => (item.checked = false));
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
  /* background-color: red; */
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
.lists ul {
  padding-left: 0px;
}
.list {
  border: 1px solid black;
  margin: 10px;
  padding: 10px;
}
select {
  border: none;
}
.items {
  display: flex;
  flex-direction: column;
  width: 200px;
}
.countBlock {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.inputItem {
  display: flex;
}
.inputColor {
  width: 20px;
  height: 20px;
  border: none;
  padding: 0px;
  margin: 0px;
}
.inputNumber {
  width: 30px;
  height: 20px;
  border: none;
}
.containerBlocks {
  display: flex;
  flex-wrap: wrap;
}
.blocksList {
  border: 1px solid black;
  margin: 10px;
  padding: 10px;
}
.blocksList ul {
  padding-left: 0px;
}
.blocksTop {
  display: flex;
  justify-content: space-between;
}
.btn {
  padding: 5px;
  margin: 15px 0px;
  background-color: rgba(0, 217, 255, 0.397);
  border: 2px solid rgb(0, 162, 255);
  border-radius: 5px;
}
.btn:hover {
  opacity: 0.8;
  cursor: pointer;
}
</style>
