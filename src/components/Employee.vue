<template>
  <div>
    <p>Name: {{ employee.name }}</p>
    <p>Age: {{ employee.age}}</p>
    <p>Compnany: {{ employee.company}}</p>
  </div>
</template>
<script>
 import axios from 'axios'
  export default {
    name: 'Employee',

    data() {
      return {
        employee: {}
      }
    },

    created() {
      this.fetchData()
    },

    watch: {
      '$route': 'fetchData'
    },

    methods: {
      fetchData() {
        axios.get('http://localhost:8082/employee/'+this.$route.params.id)
        .then((resp) => {
          this.employee = resp.data
          console.log(resp)
        })
        .catch((err) => {
          console.log(err)
        })
      }
    }
  }
</script>
You'll notice that in