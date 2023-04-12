<template>
    
    

    <info :nombre="nombre" :url="imagen" :Arryno="nombreStats" :Arrynum="numStasts" :abilities="abilities" />
</template>
<script>
export default {
    data(){
        return{
           nombre:"",
          imagen:"",
          nombreStats:[],
          numStasts:[],
          abilities:[]
        }
    },
    mounted(){
        
        this.nombre=this.$route.params.info
         this.infor();
        


    },
    methods: {

        async infor(){
            const {data} = await this.$axios.get('pokemon');
               let image=""
          
            image= await this.getpokemon(this.nombre);
            console.log(image)
            this.imagen=image
            this.Stats(this.nombre);
            this.Ability(this.nombre)
         
        },

        async getpokemon(pokeName){
          const {data} = await this.$axios.get(`pokemon/${pokeName}`);
          return data.sprites.other["official-artwork"]["front_default"]
        },

         async Stats(pokeName){
          const {data} = await this.$axios.get(`pokemon/${pokeName}`);
           
           for( let i=0; i< data.stats.length;i++){
            this.numStasts.push(data.stats[i]["base_stat"])
            this.nombreStats.push(data.stats[i]["stat"]["name"])
           }
        },        
         async Ability(pokeName){
          const {data} = await this.$axios.get(`pokemon/${pokeName}`);
           
           for( let i=0; i< data.abilities.length;i++){
            this.abilities.push(data.abilities[i]["ability"]["name"])

           }
        }



  }
   
}
</script>