<template>

 <div class="bg-[url('~/static/bgg.jpg')]  ">
   

  <div v-if="!loading" class="flex justify-center "> 
    <h1 class="flex justify-center  text-[60px] w-[40rem] bg-[#faa307] ">  Poke API </h1>

  </div>
 


 <div  v-if="!loading" class="ml-5 flex  ">
  <form action="" @submit.prevent="searchnn()">
<input type="text" name="" id="" class="border border-2 border-black" v-model="search">
  </form>
  
  <button class="ml-3 bg-[#ffba08]">Buscar </button>
 </div>
  
 <loding v-if="loading"/>

 <div class="grid grid-cols-4 px-5 mt-4 gap-[40px]">
  <card  v-for=" i in response" :key="i.name" :name="i.name" :url="i.image"  />

 </div>
   



 </div>


</template>

<script>

export default {
    name:'IndexPage',
    data(){
    return {
      response:[],
      img:[],
      search:"",
      loading:true

    }
    

  },
  mounted(){
        this.infor();
    },
  methods: {
    cambiar(){
      if (this.nombre=="Ojeda martinez"){
        this.nombre="jose fernando"
        this.mostrar=true
      }else{
        this.nombre= "Ojeda martinez"
        this.mostrar=false
      }

      
    },



        async infor(){


          try{
            const {data} = await this.$axios.get('pokemon');
       let image=""

          for( let i=0; i<data.results.length;i++){
            image= await this.getpokemon(data.results[i].name)
            data.results[i].image=image
          }
          this.response = data.results
          this.loading=false
          } catch(e){
            console.log("hubo un error")
          }

        },

        async getpokemon(pokeName){
          const {data} = await this.$axios.get(`pokemon/${pokeName}`);
          return data.sprites.other["official-artwork"]["front_default"]
        },

        searchnn(){

         


          window.location.href = `/${this.search}`

        }


  }
}
</script>
