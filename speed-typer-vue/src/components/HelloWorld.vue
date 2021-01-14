<template>
  <h1>Speed Typer</h1>
  <p>
    <span v-for="(keyword, index) in keywords" :key="index">
      {{keyword+ ' '}} 
    </span>    
  </p>
  <input type="text" :value="inputValue" @keyup.space="processInput($event)">
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return{
      index: 0,
      inputValue: '',
      keywords: ['JavaScript', 'HTML', 'CSS', 'React','Vue', 'Angular','PHP','C#', 'DotNet'],
    }
  },
  methods: {
    processInput(event){
      this.inputValue= event.target.value.trim();
      console.log(this.inputValue);
      this.inputValue=''
    }
  }

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
