<template>
 
  <div class="container center-block">
    <div class="row" align="center">
      <!--web input-->
      <div class="col-xs-8" >
        <div class="input-group input-group-lg">
          <span class="input-group-addon" id="prefix">https://</span>
          <input type="text" v-model="url" class="form-control" placeholder="Medium.com" aria-describedby="basic-addon3">
        </div>
      </div>    
    </div>
    
    <!--tag input-->
    <div class="row" >
      <div class="col-xs-12" style="margin:2em 0">
        <div class="col-xs-8">
          <input v-model="userInput" class="form-control"/>
        </div>
         <div class="col-xs-4">
        <button class="btn-primary" @click="add(userInput)">Add Tag</button>
        </div>
        <div style="margin:1em 0;">
          <span class="chip" v-for="(tag, index) in tags" :key="tag" id="tag"> {{tags[index]}} <span @click="remove(tag)"> X </span> </span>
        </div>
      </div>
    </div>  
      
      <div class="column" style="margin-top:3em" >
        <button class="btn btn-lg" @click="scrape()">Scrape</button>
        <!--<button class="button-large button-outline">Reset</button>-->
      </div>
   
    <div class="row">
      <div class="column">
        <h3>Results:</h3>
        {{data}}
      </div>
    </div>
 </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'hello',
  data () {
    return {
      url: '',
      tags: [],
      data: null,
      userInput:null
    }
  },
  methods : {
    scrape(url, tag){
      let self = this;
      // axios.get(`http://localhost:3000/scrape?url=http://${this.url}&tag=${this.tag}`)
      axios.post(`http://localhost:3000/scrape`, this.tags)
        .then( (response) => {
          self.data = response.data;
        })
        .catch( (error) => {
          console.log(error);
          self.data = 'There was an error'
        });
    },
    add(userInput){
      if(userInput !== null){
        this.tags.push(userInput);
      }
    },
    remove(index){
      this.tags.pop(index);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}
#prefix{
  color:grey;
  background:lightgrey;
  border:none;
}
li {
  display: inline-block;
  margin: 0 10px;
}
#tag{
  background:1em;
  color:grey;
  border:1px solid grey;
  border-radius:5px;
  padding:.3em 2em;
  margin:0 1em;
}
a {
  color: #42b983;
}
</style>
