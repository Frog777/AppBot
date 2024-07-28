<script>
export default{
  data(){},
  props:{
    activBasket:{ type:Function,require:true,},
    homeList: {type:Function,require:true,},
    //chekingForCount:{type:Function,require:true,},
  }}

</script>

<template>
    <header class="bg-white bg-opacity-50 mb-3 rounded-xl shadow-xl flex justify-between p-5 m-autо">
      <div class="w-12 cursor-pointer" @click="homeList()">
        <img src="/house.png" alt="home">
      </div>

        <div class="w-14 cursor-pointer " @click="activBasket()">
         <img src="/bag.png" alt="home">
        </div>
</header>
</template>