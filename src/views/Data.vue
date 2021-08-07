<template>
  <v-data-table
    :headers="headers"
    :items="data"
    sort-by="calories"
    class="elevation-1"
  >
    <!-- Action update and delete -->
    <template v-slot:item.actions="{ item }">
      <!-- <v-icon
        small
        class="mr-2 blue--text"
        @click="editdata(data)"
      >
        mdi-pencil
      </v-icon> -->
      <v-icon
        small
        class="red--text"
        @click="deleteForm(item._id)"
      >
        mdi-delete
      </v-icon>
    </template>
  </v-data-table>
  
</template>

<script>
import axios from 'axios'

export default {
  data: function(){
    return {
      result: null,
      headers: [
        { text: 'id', value: '_id' },
        { text: 'name', value: 'name' },
        { text: 'email', value: 'email' },
        { text: 'dob', value: 'dob' },
        { text: 'address', value: 'address' },
        { text: 'phone', value: 'phone' },
        { text: 'creation date', value: 'createAt' },
        { text: 'actions', value: 'actions', sortable: false },
        
      ],
      data: []
    }
  },
  mounted() {
    this.getData()
  },
  methods: {
    getData: function(){
      axios({
        method: 'get',
        url: 'http://localhost:3300/forms/',
      }).then(response => {
        const results = response.data;
        if(results.status === true){
          console.log(results.data)
          this.data = results.data
        }
      }).catch(error => {
        console.log(error)
      })
    },
    deleteForm: function(id){
      axios({
        method: 'get',
        url: 'http://localhost:3300/forms/delete/'+id,
      }).then(response => {
        const results = response.data;
        if(results.status === true){
          console.log(results.data)
          this.getData()
        }
      }).catch(error => {
        console.log(error)
      })
    }
  },
  computed: {

  },
}
</script>