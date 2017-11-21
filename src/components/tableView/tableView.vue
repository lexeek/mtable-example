<template>
  <div class="tableView">
    <button v-bind:disabled="isButtonDisabled" v-on:click="toggleTable">Toggle Table</button>
    <div v-if='isTableVisible'>this is material table <span>{{currentTime}} {{showTime()}}</span> <br>

      <span><data-table :currentPage=currentPage :sortable=sortable :columns=columns :rows=rows
                        :perPage=perPage></data-table></span>
    </div>
  </div>
</template>

<script>
  import DataTable from 'vue-materialize-datatable'
  import * as axios from 'axios'

  export default {
    components: {DataTable},
    name: 'tableView',
    data () {
      return {
        currentPage: 10,
        sortable: true,
        perPage: [5, 10, 25, 50, 500],
        columns: [
          {
            label: 'Id',  // Column name
            field: 'id',  // Field name from row
            // Use dot for nested props
            // Can be function with row as 1st param
            numeric: true, // Affects sorting
            html: false    // Escapes output if false.
          },
          {
            label: 'Name',  // Column name
            field: 'name',  // Field name from row
                            // Use dot for nested props
                            // Can be function with row as 1st param
            numeric: false, // Affects sorting
            html: false    // Escapes output if false.
          },
          {
            label: 'Email',  // Column name
            field: 'email',  // Field name from row
            // Use dot for nested props
            // Can be function with row as 1st param
            numeric: false, // Affects sorting
            html: false    // Escapes output if false.
          },
          {
            label: 'Username',  // Column name
            field: 'username',  // Field name from row
            // Use dot for nested props
            // Can be function with row as 1st param
            numeric: false, // Affects sorting
            html: false    // Escapes output if false.
          },
          {
            label: 'Website',  // Column name
            field: 'website',  // Field name from row
            // Use dot for nested props
            // Can be function with row as 1st param
            numeric: false, // Affects sorting
            html: false    // Escapes output if false.
          }
        ],

        rows: [                       // Array of objects
          {
            name: 'test'   // Whatever.
          }
        ],
        isTableVisible: false,
        isButtonDisabled: false,
        currentTime: `${new Date().getHours()}:${new Date().getMinutes()}:${new Date().getSeconds()}`
      }
    },

    created: function () {
      this.fetchData()
    },
    methods: {
      showTime () {
        setInterval(() => {
          this.currentTime = `${new Date().getHours()}:${new Date().getMinutes()}:${new Date().getSeconds()}`
        }, 1000)
      },

      fetchData () {
        let vm = this
        axios.get('https://jsonplaceholder.typicode.com/users')
          .then(function (response) {
            console.log('response', response.data)
            vm.rows = response.data
          })
      },
      toggleTable () {
        this.isTableVisible = !this.isTableVisible
      }
    },
    mounted () {

    }
  }
</script>

<style lang='scss'>

  .material-table {
    li {
      list-style: none !important;
      margin-top: 0 !important;
    }
  }

  /*}*/
</style>
