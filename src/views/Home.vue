<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div 
    :style="{color:store.state.colorCode}"
    class="counter">
      {{store.state.counter}}
    </div>
    <div class="countersquared">
      {{store.state.counter}}
      <sup>2</sup> = 
      {{store.getters.countersquared()}}
    </div>
    <div class="buttons">
        <button  @click = 'store.methods.decreaseCounter'>-</button>
        <button @click = 'store.methods.increaseCounter'>+</button>
    </div>

    <input v-model = 'colorCode' type="text" placeholder="enter color code">
  </div>
 
</template>

<script>
// @ is an alias to /src

import {inject,computed} from 'vue'
export default {
  name: 'Home',
  setup() {
    const store = inject('store')

    const colorCode = computed({
        get(){
          return store.state.colorCode
        },
        set(val){
          store.methods.setColorCode(val)
        }

    })


  

  
     return {store,colorCode}
  }
 
}
</script>
<style>
.counter{
  font-size: 80px;
}
.buttons button{
  font-size: 60px;
  width: 100px;
  margin: 0 10px;
}
</style>
