<template>
<div class="bg-[url('~/static/fondo.jpg')] bg-cover h-screen">

  

    <p class="flex justify-center text-[60px]">{{nombre}}    </p>
 <div class="m-7 flex flex-row w-[100rem] justify-between">
     <img :src="url" class="w-[20rem]" alt="">


     <div class="w-[50rem] h-[20rem] border-dotted border-2 border-black ">
     


        <div class=" flex"> 
            <div class="w-96" >
           
                <h1 class="flex justify-center ">Stats</h1>  
    
               <div class="flex flex-row justify-center mt-5">
                   <div>
                       <li v-for=" i in Arryno "> {{ i }}: </li>
                   </div>
               <div class="pl-3">
                   <p v-for=" j in Arrynum"> {{j}}</p>
               </div>
           
                  </div>
         </div>


         <div class="w-96" >
           
            <h1 class="flex justify-center ">Abilities</h1>  

           <div class="flex flex-row justify-center mt-5">
               <div>
                   <li v-for=" o in abilities "> {{ o }}</li>
               </div>

       
              </div>
     </div>
        </div>




     

  

  </div>





 </div>
 <p class="flex justify-center text-[40px]">Imagenes    </p>
</div>




</template>

<script>
 export default {
    props: {
    nombre: {
        type: String,
        required: true
    },
    url:{ type: String, required: true},
    Arryno:{ type: Array, required: true},
    Arrynum:{  type: Array, required: true},
    abilities:{ type: Array, required: true}
}
 }


</script>