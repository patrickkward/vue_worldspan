<template>
  <div>
    <li v-bind:key="item.message" v-for="item in items">{{ item.message }}</li>
    <p> {{ temp }} </p>
  </div>
</template>

<script>
/* eslint-disable */
import axios from 'axios'

export default {
  name: 'ListRender',
  data () {
    return {
      temp: String
    }
  },
  components: {
  },
  props: {
    items: Array
  },

  created () {
    this.printAxios()
  },

  methods: {
    printAxios () {
      axios.get(`http://localhost:8000/api/things/`).then(response => {
        debugger
        this.temp = response.data
      }).catch(e => {
        console.log(e)
      })
    }
  }
}

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
