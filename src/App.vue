<template>
  <div id="app" class="deliveryListContainer">
    <div class="heading">
      <h2 id="title">Available delivery</h2>      
    </div>  
    <div> 
      <span class="item"> Select city</span>
      <select name="check city" id="" 
        @change="onChange($event)" v-model="key">
        <option selected value="nur-sultan">Нур-Султан</option>
        <option value="almaty">Алматы</option>
        <option value="semey">Семей</option>
        <option value="aktobe">Актобе</option>
      </select>
    </div>
    <div class="item">
      <span>City</span>
      <span>Type</span>
      <span>Price</span>
      <span>Available</span>
    </div>
    <hr> 
    <list-view :items="items"/>
  </div>
</template>

<script>
import listView from './components/listView.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    listView
    
  },
  data(){
    return {
      items: [],
      key: "",
      url: `http://localhost:3000/delivery/check?search=`,
      city: 'nur-sultan'
    }
  },
  methods: {
    onChange(event) {            
            this.city = event.target.value
            console.log(this.city)
            this.getList()
    },
    getList(){
      axios.get(this.url+this.city)
      .then( response => {
        this.items = response.data
        console.log(this.items)
      })
      .catch( error => {
        console.log( error );
      })
    }    
  },
  created(){
    this.getList()
  }

}
</script>

<style scoped>
 .deliveryListContainer{
        width: 450px;
        margin: auto;
  }
  .heading {
      background: #e6e6e6;
      padding: 10px;
  }
  #title {
      text-align: center;
  }
  .item {
    background: #e6e6e6;
    font-weight: bold;
    padding: 5px;
    margin-top: 5px;
  }
  span {
    padding-right: 80px;
  }  
  select {
    margin: 10px 0;
    width: 200px;
    /* border-radius: 5px; */
    height: 28px;
  }
</style>
