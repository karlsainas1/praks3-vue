<template>
  <div>

 
   <h1>Numbri faktid</h1>
  <input type="number" placeholder="sisesta number" min="0" v-model="number" >
       <input type="number" placeholder="sisesta inc" min="0" v-model="inc" >
           
      <p v-for="value in data" :key="index"> {{ value }} </p>
                
</div>
</template>

<script>
    const axios = require('axios')
export default {
  name: 'Faktid',
  data(){
      return{
      
          data:'',
        number: 0, 
        inc:0
      }
  
  },
    watch:{
        number(){
            this.getResponse()
        },
        inc(){
            this.getResponse()
        } 
    },

        
    
    methods:{
       
        getResponse () {
            if(this.number !== '' && this.inc !== '')  {   
                
                let url = `http://numbersapi.com/${this.number}..${this.inc}`     
                   
        
                axios.get(url)
                    .then(response => {
                      this.data=response.data
                    items=response.data
                })
                .catch(error =>{
                    console.log(error)
                })
        
            }
        
           
           
           
       }
    },
   
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    
    
    
</style>
