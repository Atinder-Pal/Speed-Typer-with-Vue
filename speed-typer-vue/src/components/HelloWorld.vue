<template>
  <h1>Speed Typer</h1>
  <p>
    <span 
      :class="{ correct: keyword.correct, wrong: keyword.wrong, pending: keyword.pending}"
      v-for="keyword in keywords" :key="keyword.text">
      {{keyword.text + ' '}} 
    </span>    
  </p>
  <input type="text" :value="inputValue" @keyup.space="processInput($event)">
</template>

<script>
const defaultKeywords = ['JavaScript', 'HTML', 'CSS', 'React','Vue', 'Angular','PHP','C#', 'DotNet'].map(keyword => {
  return {
    text: keyword,
    correct: false,
    wrong: false,
    pending: true
  }
});
export default {
  name: 'HelloWorld',
  data() {
    return{
      index: 0,
      inputValue: '',
      keywords: defaultKeywords,
    }
  },
  methods: {
    processInput(event){
      this.inputValue= event.target.value.trim();
      console.log(this.inputValue);
     
      if (this.inputValue === "") {
        return;
      }
      if(this.keywords[this.index].text === this.inputValue) {
        this.keywords[this.index].correct = true
        this.keywords[this.index].pending = false                
      } else {
        this.keywords[this.index].wrong = true
        this.keywords[this.index].pending = false
      }
       this.inputValue='';
       this.index++;
    },
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
.pending {
  font-weight: bold;
}
.wrong {
  font-weight: bold;
  color: red;
}
.correct{
  font-weight: bold;
  color: green;
}

</style>
