<template>
  <div class="container">
    <div class="input-group mb-3">
      <label for="inputText">Input Text: </label>
      <input v-model="inputText" type="text" name="inputText" class="form-control" id="input" placeholder="Input text">
      <button @click="group" class="btn btn-primary">Group Text</button>
    </div>
    <p>Grouped text is: {{this.groupedText}}</p>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
export default {
  name: 'Chargrouper',
  data() {
    return {
      inputText:'',
      groupedText:''
    }
  },
  methods: {
     async group(){
       const result = await fetch(`http://localhost:8080/chargrouper/${this.inputText}`);
       const data = await result.json();
       this.groupedText = data.groupedStr;
       console.log(data);
     } 
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  width: 60%;
} 
#input{
  width: 30%;
}
label{
  float: left;
  margin-top: 5px;
  margin-right: 10px;
  margin-left: 30px;
  font-size: large;
}
button{
  margin-left: 10px;
}
p{
  float: left;
  font-family: Arial, Helvetica, sans-serif;
  font-size: larger;
}
</style>
