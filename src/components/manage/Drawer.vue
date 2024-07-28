<script>
export default{
    data(){
        return{
           
        }
    },
    props:{
        date:{type:Array,require:true},
        listOfAll:{type:Array,require:true}
    },
         methods:{
            ink(index){
                this.listOfAll[index].count++
                this.listOfAll[index].price+=this.listOfAll[index].total
                
            },
            dik(index){
                if(this.listOfAll[index].count>1) {
                    this.listOfAll[index].count--
                    this.listOfAll[index].price-=this.listOfAll[index].total
                }else{
                    this.listOfAll.splice(index,1)
                }
            },
    }
}



</script>
<template>
    <!-- WRAPER -->
    <div  class="bg-white  rounded-xl bg-opacity-50 pt-10 pb-1 px-px justify-center justify-items-center items-center text-xl " >

        <!-- отображение что показать список или сказать что пусто -->
     <div v-if="listOfAll.length>0">
        <!-- Итерируемая строка -->
        <div class="px-8 grid grid-col-3 mb-10" v-for="(val,index) in listOfAll" :key="index">
            <!-- НАЗВАНИЕ -->
            <div  class="col-start-1 col-end-1 justify-items-start" ><p>{{ val.name }}</p></div>
            <!-- ЦЕНА -->
            <div  class="col-start-2 col-end-2 justify-items-start" ><p>{{ val.price }}р.</p></div>
            <!-- УВЕЛИЧЕНИЕ УМЕНЬШЕНИЕ -->
            <div class="col-start-3 col-end-3 flex justify-end">
                <div class="rounded-xl  bg-lime-500 w-10 h-10 flex justify-center items-center" @click="ink(index)">+</div>
                <p class="mr-3 ml-3 flex justify-center items-center">{{ val.count }}</p>
                <div class="rounded-xl  bg-lime-500 w-10 h-10 flex justify-center items-center" @click="dik(index)">-</div>
            </div>

           
       </div><!--  Итерируемая строка -->
       <div class="flex justify-center mb-5 hover:-translate-y-2 transition mt-10"><button class="bg-lime-500 rounded-xl h-10 pl-20 pr-20" type="button">Оформить заказ</button></div>
    </div>



    <!-- КНОПКА ОФОРМИТЬ -->
    <div class="flex justify-center mb-10 bold" v-else><p class="text-xl">Ваша корзина пуста!</p> </div>
        
    </div>
</template>