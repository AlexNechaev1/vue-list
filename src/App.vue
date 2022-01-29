<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <ItemForm  v-on:onSubmit='submitItem'/>
    <ListItem v-bind:list="items" v-on:onDelete="deleteItem" />
  </div>
</template>

<script>
import ItemForm from "./components/ItemForm/ItemForm.vue";
import ListItem from "./components/listItem/ListItem.vue";
import { loadData, saveData} from "./localData";

const listItem = loadData("items");

export default {
  name: "App",
  data() {
    return {
      items: listItem,
    };
  },
  methods: {
    submitItem(item){
      this.items.push(item);
      saveData('items',this.items);
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      saveData('items',this.items);
    },
  },
  components: {
    ItemForm,
    ListItem,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
