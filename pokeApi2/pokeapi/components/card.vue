<template>
    <nuxt-link :to="name" class="">
        <div class="w-96 h-[30rem] bg-[#d00000] border border-2 border-black ">
            <div id="tipo"  >
                <div class="flex justify-center" id="conter" >
                <img :src="url" class="w-[20rem]" alt="...">
                </div>
                
                <div class="grid justify-items-center " >
                  <h2 class="">{{name}}</h2>
                  <h5 class="card-text">habilidades</h5>
                  <a id="ir" href="index.html" class="btn btn-primary">Go somewhere</a>
                </div>
                </div>
        </div>

    </nuxt-link>
</template>


<script>


export default {

props: {
    name: {
        type: String,
        required: true
    },
    url:{ type: String, required: true}
}
}

</script>