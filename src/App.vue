<template>
  <div id="app">

    <Headbook @childtoParent="getSearchValue"></Headbook>   
    <Bookstore :dataEnglish="filteredDataEnglish"></Bookstore>
    
    
  </div>
</template>

<script>

import Headbook from './components/Headbook.vue'
import Bookstore from './components/Bookstore.vue'


export default {
  name: 'App',
  components: {

    Headbook,
    Bookstore,
    
    
    
    
  },
  data(){ 
      return { 
        dataEnglish: [],
        search: ""

      }
    }, 
  computed: {
      filteredDataEnglish() {
        return this.dataEnglish.filter(showPortada => {
          return showPortada.titulo.toLowerCase().includes(this.search.toLowerCase())
        })
      }
    },

  methods:{
      doRequest(){
                fetch('https://api.myjson.com/bins/1h3vb3', {
                method: "GET",
            })
            .then( (response)=> {
                return response.json();
            }).then((dataFromServer) => {
                console.log(dataFromServer)
                this.dataEnglish = dataFromServer.books;     
                         
            })
        },
       getSearchValue(value) {
         console.log (value)
         this.search = value
    }

        },
    created(){
            this.doRequest(); 
        }

  } 
   
</script>

