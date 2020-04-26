<template>
    <div class="flex-container">
        <div class="flip-card" v-for="showPortada in dataEnglish" v-bind:key="showPortada.portada">
            <div class="flip-card-inner">
                <div class="flip-card-front">                     
                    <img :src="showPortada.portada" width="100%" height="100%">          
                </div>   
                <div class="flip-card-back">
                    <h3>{{showPortada.titulo}}</h3>         
                    <p>{{showPortada.descripcion}}</p>  
                    <!-- <button Mas Info -->
                    <a :href="showPortada.portada" data-fancybox="images" >  
                     <button>Mas Info </button>  
                     </a>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
export default {
  name: 'Bookstore',
  props:['dataEnglish'],
  data(){ 
      return { 
       
      }
},  
  methods:{
      doRequest(){
                fetch('https://api.myjson.com/bins/1h3vb3', {
                method: "GET",
            })
            .then(function (response) {
                return response.json();
            }).then((dataFromServer) => {
                console.log(dataFromServer)
                this.dataEnglish = dataFromServer.books;                
            })
        }

        },
    created(){
            this.doRequest(); 
        }

  }
</script>