<template>
 <div>

 <h1 class="flex justify-center  text-[60px]">  Poke API </h1>


 <div>
  <input type="text" name="" id="" class="border border-2 border-black">
  <button class="">Buscar</button>
 </div>
  
   

 <div class="grid grid-cols-4 px-5 mt-4 gap-[40px]">
  <card  v-for=" i in response" :key="i.name" :name="i.name" :url="i.image"  />

 </div>
   


    <info/>
 </div>


</template>

<script>

export default {
    name:'IndexPage',
    data(){
    return {
      response:[],
      img:[],

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
            const {data} = await this.$axios.get('pokemon');
       let image=""

          for( let i=0; i<data.results.length;i++){
            image= await this.getpokemon(data.results[i].name)
            data.results[i].image=image
          }
          this.response = data.results
        },

        async getpokemon(pokeName){
          const {data} = await this.$axios.get(`pokemon/${pokeName}`);
          return data.sprites.other["official-artwork"]["front_default"]
        }



  }
}
</script>
