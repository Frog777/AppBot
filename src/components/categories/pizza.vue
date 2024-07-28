<script>
import Card from "../manage/Card.vue"


export default{
    components: {Card,},
    data(){
        return{button:true,quality:-1,}},
        props:{listOfAll:{type:Array,require:true},},

        methods:{
            changeButton(index){
            this.quality=index
            if(this.listOfAll[index].count==0){this.listOfAll[index].count++}
            },

            ink(index){
                this.listOfAll[index].count++
                this.listOfAll[index].price+=this.listOfAll[index].total
            },
            dicrement(index){
                if(this.listOfAll[index].count>1) {
                    this.listOfAll[index].count--
                    this.listOfAll[index].price-=this.listOfAll[index].total
                }else{
                    this.quality=-1
                }

            }
        }

}

</script>

<template>
    <Card v-for="(val,index) in listOfAll" :key="index" >
        <p>{{ val.name }}</p>
        <img src="/rolls.jpg" alt="img">
        <p>{{ val.price }}р.</p>
        <div class="flex justify-center mb-5 transition">
            <button v-if="quality!=index" @click="changeButton(index)" class="bg-lime-500 rounded-xl  pl-5 pr-5" >Добавить</button>
            <div v-else-if="quality==index" class="col-start-3 col-end-3 flex justify-end">
                <div class="rounded-xl  bg-lime-500 w-9 h-9 flex justify-center items-center" @click="ink(index)">+</div>
                <p class="mr-3 ml-3 flex justify-center items-center">{{ val.count }}</p>
                <div class="rounded-xl  bg-lime-500 w-9 h-9 flex justify-center items-center"  @click="dicrement(index)">-</div>
            </div>
        </div>
    </Card>
</template>