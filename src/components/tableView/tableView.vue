<template>
  <div class="tableView">
    <button v-bind:disabled="isButtonDisabled" v-on:click="toggleTable">Toggle Table</button>
    <div v-if='isTableVisible'>this is material table <span>{{currentTime}} {{showTime()}}</span> <br>

      <span><data-table :columns=columns :rows=rows :perPage="[100, 10, 25, 50, 500]"></data-table></span>
    </div>
  </div>
</template>

<script>
  import DataTable from 'vue-materialize-datatable'

  export default {
    components: {DataTable},
    name: 'tableView',
    data () {
      return {
        columns: [                       // Array of objects
          {
            label: 'Name',  // Column name
            field: 'name',  // Field name from row
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

    methods: {
      showTime () {
        setInterval(() => {
          this.currentTime = `${new Date().getHours()}:${new Date().getMinutes()}:${new Date().getSeconds()}`
        }, 1000)
      },
      toggleTable () {
        this.isTableVisible = !this.isTableVisible
      }
    }
  }
</script>

<style scoped lang='scss'>

  .material-table{
    li {
      list-style: none;
    }
  }
</style>
