
<template>
    <div class="bloco">
      <ul type="none" class="numeros">
        <li v-for="numero in dezenas" v-bind:key="numero">
          {{ numero }}
        </li>
      </ul>
      <button @click="gerarNumero()" class="botao">Gerar</button>
    </div>
  </template>
  
  <script>


  export default {
    name: 'PaginaInicial',
    data:()=>({
     dezenas:[]
    }),
    methods:{
        numeroAleatorio(){
        let numeros = Math.floor(Math.random()*(60)+1)
        return numeros
        },
        gerarNumero(){

         for(let i=0;i<=5;i++){
          let numeros = this.numeroAleatorio()
          let elemento = this.dezenas.indexOf(numeros)
          if(elemento !=-1 ){
          
           while(elemento != -1){
            numeros = this.numeroAleatorio()
            elemento = this.dezenas.indexOf(numeros)
           }
           this.dezenas[elemento] = numeros
         
          }else{
          this.dezenas[i] = numeros
         }
         }

         for(let n=0;n<=5;n++){
          if(this.dezenas[n] == null){
          let numeros = this.numeroAleatorio()
          let elemento = this.dezenas.indexOf(numeros)
          while(elemento != -1){
            numeros = this.numeroAleatorio()
            elemento = this.dezenas.indexOf(numeros)
           }
           this.dezenas[n] = numeros
      
          }
          if(this.dezenas[n]<=9){
            console.log(typeof(this.dezenas[n]))
             if(typeof(this.dezenas[n]) != 'string'){
              this.dezenas[n] = '0'+this.dezenas[n]
            }
          }
         }
        }
    }
  }
 
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>

   .numeros li{
    display: inline;
    padding: 10px;
    margin: 10px;
    background-color: green;
    color: aliceblue;
    border-radius: 100px;
    font-size: 30px;
    width: 50%;
    
   }
   .numeros{
    position: absolute;
    left: 30%;
   }
   .botao{
    background-color: aqua;
    font-family: 'Times New Roman', Times, serif;
    font-size: 20px;
    padding: 5px;
    width: 200px;
    border: none;
    border-radius: 50px;
    box-shadow: 1px 1px 20px 0  rgb(217, 219, 221);
    position: absolute;
    top:85%;
    left: 35%;
   }
   .botao:hover{
    cursor: pointer;
   }
   .bloco{
    background-color: rgb(247, 249, 252);
    box-shadow: 1px 1px 20px 0 rgb(217, 219, 221);
    width: 500px;
    height: 250px;
    position: fixed;
    border-radius: 10px;
    left: 40%;
   }
   @media(max-width: 500px){
    .numeros li{
      display: block;
    }
    .bloco{
      height: 500px;
      width:400px;
      left: 1.5%;
    }
    .botao{
      left:25%;
    }
   }
   @media (orientation:landscape){
    .numeros li{
      display: inline;
      width: 2px;
      margin: 2px;
      font-size: 20px;
      

    }
    .numeros{
      left: 0%;
    }
    .bloco{
      height: 250px;
      width:350px;
      left: 25%;
      top:5%
     
    }
    .botao{
      left:25%;
    }
   }
  </style>
  