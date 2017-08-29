<template>
 
  <div class="container">
    <div class="row">
      <div class="column column-40">
        <label for="nameField">WEBSITE</label>
        <input type="text" v-model="website" placeholder="medium.com" id="nameField">
      </div>
      <div class="column column-20">
        <label for="nameField">HTML TAG</label>
        <input type="text" v-model="tag" placeholder="h1,p,li" id="nameField">
      </div>
      <div class="column column-40 float-left" style="margin-top:2em" >
        <button class="button-large">Scrape</button>
        <button class="button-large button-outline">Reset</button>
      </div>
    </div>
    
    <div class="row">
      <div class="column">
        
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      website: '',
      tag
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

.button-large {
  font-size: 1.4rem;
  height: 4.5rem;
  line-height: 4.5rem;
  padding: 0 2rem;
}
</style>
