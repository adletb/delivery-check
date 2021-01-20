<template>
  <div class="item" :class="[!item.available ? 'completed' : '']">     
      <span class="capital"> {{ item.city }} </span>
      <span> {{ item.type }} </span>
      <span> {{ item.price }} </span>
      <span v-if="item.available"> Yes </span>
      <span v-else > No </span>
   </div>
</template>

<script>
export default {
    props: ['item']
}
</script>

<style scoped>
    .completed{
        text-decoration: line-through;
        color: #999999;
    }
    .itemText {
        width: 100%;
        margin-left: 20px;
    }
    .item {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .trashcam{
        background: #e6e6e6;
        background: none;
        color: #FF0000;
        outline: none;
    }
    span {
       width: 120px;
    }
    .capital{
    text-transform: capitalize;
    }  
</style>
