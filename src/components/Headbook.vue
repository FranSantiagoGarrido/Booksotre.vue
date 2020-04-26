<template>
  <div id="app">
    <div class="row">
      <div class="col">
        <img src="@/assets/logoubiqum.png"  width="85%" height="80%">
      </div>      
      <div class="col">
        <div class="col d-flex justify-content-start align-items-flex-end">
          <div class="main">
            <div class="form-group has-search">
             <span class="fa fa-search form-control-feedback"></span>
              <input type="text" v-model="search" placeholder="Search" @keyup="emitToParent">
            </div>
          </div>
        </div>
      </div>
    </div>       
  </div>
</template>

<script>
export default {
  name: 'Headbook',
  props:{
   
        
            
  },
  data(){ 
      return { 
        search:''
      }
}, 
methods: {

    emitToParent (){
        this.$emit("childtoParent",this.search)
    }
}
    
}

</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  
}

.flip-card {  
  background-color: transparent;
  width: 300px;
  height: 450px;
  margin: 25px;
  perspective: 1000px;  
  
}

.flip-card-inner {

  position:relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);

  
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {  
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  
  
}

.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  background-color: #2980b9;
  color: white;
  transform: rotateY(180deg);
}
.flex-container {

  display: flex;
  flex-wrap: wrap;  
  height: 600px;
  justify-content: space-between; 
   
}



/* Search box */

.main {
  width: 50%;
  margin: 50px auto;
}
.has-search .form-control {
  padding-left: 2.375rem;
}
.has-search .form-control-feedback {
  position: absolute;
  z-index: 2;
  display: block;
  width: 2.375rem;
  height: 2.375rem;
  line-height: 2.375rem;
  text-align: center;
  pointer-events: none;
  color: #aaa;
}
</style>
