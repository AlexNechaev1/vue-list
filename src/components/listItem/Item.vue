<template>
  <div>
    <div id="item-container">
      <div id="item-details">
        <div class="item-text item-index">{{ id }}</div>
        <div class="item-text item-name">{{ itemName }}</div>
      </div>
        <div class="item-text">{{ itemDescription }}</div>
      <div class="item-text item-del-btn" v-on:click='onDeleteHandler'>Delete</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    id: String,
    index:Number,
    itemName: String,
    itemDescription: String,
  },
  methods:{
    onDeleteHandler(){
        this.$emit('onDelete',this.index);
    }
  },

};
</script>

<style scoped>
#item-container {
  background-color: #43b883;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.1rem 20rem;
  padding: 1rem 3rem;
  border: none;
  border-radius: 3rem;
}
#item-container:hover {
  background-color: #5ed8a1;
}
#item-details{
    
    
}
.item-text {
  background-color: white;
  padding: 0.2rem 0.6rem;
  border: none;
  border-radius: 1rem;
  text-align: center;
}
.item-index{
    border-radius: 1rem 1rem 0 0;
}
.item-name{
    border-radius: 0 0 1rem 1rem;
}
.item-del-btn {
  background-color: crimson;
  padding: 1em;
  color: white;
}

.item-del-btn:hover {
  background-color: tomato;
  color: black;
}
</style>
