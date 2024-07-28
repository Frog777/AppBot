<script>
import Header from './components/manage/Header.vue'
import CardsList from './components/manage/CardsList.vue'
import Drawer from './components/manage/Drawer.vue'
import Card from "./components/manage/Card.vue"
import rolls from "./components/categories/rolls.vue"
import pizza from "./components/categories/pizza.vue"
import burger from "./components/categories/burger.vue"













export default{
    components: {Header,CardsList,Drawer,Card,pizza,rolls,burger},
data(){
    return{
        activ:true,
        showBag:false,
        activCategories:true,

        categories:["Rolls", "Pizza", "Hot", "Cold Sneck"],
        listOfAll:[[],

                [{name:"Филадельфия",price:450,count:0,total:450},
                {name:"Калифорния",price:350,count:0,total:350},
                {name:"Канада",price:550,count:0,total:550},
                {name:"Азуми",price:250,count:0,total:250},
                {name:"Киото",price:400,count:0,total:400},],

                [{name:"Пеперони",price:450,count:0,total:450},
                {name:"Маргаритта",price:350,count:0,total:350},
                {name:"Цезарь",price:550,count:0,total:550},
                {name:"Ветчина",price:250,count:0,total:250},
                {name:"Грибы",price:400,count:0,total:400},],

                [{name:"Чикен",price:450,count:0,total:450},
                {name:"Говяжий",price:350,count:0,total:350},
                {name:"С курицей",price:550,count:0,total:550},
                {name:"С индейкой",price:250,count:0,total:250},
                {name:"с Грибы",price:400,count:0,total:400},],
            ],
        
        
        indexPage: null,
        hiddenCategories:true,

    }},


        methods:{
activBasket(){

    if (this.showBag==false){
        this.showBag=true;
        this.activ=false

        //ДОБАВЛЕНИЕ В МАССИВ ЭЛЕМЕНТОВ КОТОРЫЕ ОТОБРАЖАЮТСЯ В КАРЗИНЕ
        
        this.listOfAll[0]= Array.from(new Set(this.listOfAll[0].filter(el=> el.count>=1)))
        

    }else{
        this.showBag=false
        this.activ=true

        
        this.listOfAll.forEach((el)=>this.listOfAll[0].push(...el))
    }
},
 

homeWindow(){
        if(this.showBag==true || this.activCategories==false){
            this.showBag=false;
            this.activCategories=true
            this.activ=true
            this.indexPage=null
        }
        },
insertIndex(index){
                this.activCategories=false
                this.indexPage=index;},


    }}
</script>



<template>
<!-- WRAPPER -->
<div class="bg-gradient-to-r  from-pink-500 to-yellow-500 w-90 m-auto h-full rounded-xl mt-5 transition">
<Header :activBasket = "activBasket" :homeList="homeWindow" />


<Drawer v-show="showBag" :listOfAll="listOfAll[0]" />

<!-- CARDS--> 
<CardsList v-show="activ" >
<Card v-for="(val,index) in categories" :key="index" @click="insertIndex(index)" v-show="activCategories">
<p>{{ val }}</p>
<img class="mb-5" src="\rolls.jpg" alt="img">
</Card>

<rolls v-if="indexPage==0" :listOfAll="listOfAll[1]"/>

<pizza v-if="indexPage==1" :listOfAll="listOfAll[2]"/>

<burger v-if="indexPage==2" :listOfAll="listOfAll[3]"/>


</CardsList>
<!-- /CARDS--> 





<!-- /WRAPPER -->
</div>

</template>
