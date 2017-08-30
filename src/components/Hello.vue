<template>
 
  <div class="container">
    <div class="row">

      <!--user input-->
      <div class="column">
        <label for="nameField">WEBSITE</label>
        <input type="text" v-model="url" placeholder="medium.com" id="nameField">
      </div>

      <div class="column">
        <label for="tags">HTML TAG</label>
        <select id="tags" v-model="tag">
          <option value="h1">H1</option>
          <option value="h2">H2</option>
          <option value="h3">H3</option>
          <option value="p">p</option>
          <option value="li">li</option>
          <option value="td">td</option>
        </select>
        <span>Selected: {{ tag }}</span>
      </div>
      
      <div class="column" style="margin-top:1.8em" >
        <button class="button-large" @click="scrape()">Scrape</button>
        <!--<button class="button-large button-outline">Reset</button>-->
      </div>
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
      tag: '',
      data: null
    }
  },
  methods : {
    scrape(url, tag){
      let self = this;
      axios.get(`http://localhost:3000/scrape?url=http://${this.url}&tag=${this.tag}`)
        .then( (response) => {
          self.data = response.data;
        })
        .catch( (error) => {
          console.log(error);
          self.data = error;
        });
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

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
input{
  padding: 2.1rem 1.0rem;
  font-size:1em;
  display: inline-block;
  transition:ease all .5s;
    &:focus{
    opacity:1;
    transform:scale(1.1,1.1);
  }
}
select{
  transition:ease all .5s;
  &:focus{
    opacity:1;
    transform:scale(1.1,1.1);
  }
}
#tags{
  padding: 2.1rem 1.0rem;
}
.button-large {
  font-size: 1.4rem;
  height: 4.5rem;
  line-height: 4.0rem;
  padding: 0 4rem;
  background-color:#2f2f2f;
  border:2px solid #2f2f2f;
  transition:ease all .5s;
  opacity:.80;
  &:hover{
    opacity:1;
    transform:scale(1.1,1.1);
  }
}
</style>
