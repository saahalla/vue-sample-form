<template>
  <v-container>
    <v-row wrap class="xs12 sm6 md6 lg6">
      <v-col>
        <v-card
          outlined
          class="pa-6"
          max-width="600px"
        >
          <v-card-title class="pa-0 mb-4">Create New Form</v-card-title>

          <v-text-field label="name" :rules="rule" hide-details="auto" v-model="data.name"></v-text-field>
          <v-text-field label="email" :rules="rule" hide-details="auto" v-model="data.email"></v-text-field>
          <v-text-field label="dob" :rules="rule" hide-details="auto" v-model="data.dob"></v-text-field>
          <v-text-field label="address" :rules="rule" hide-details="auto" v-model="data.address"></v-text-field>
          <v-text-field label="phone" :rules="rule" hide-details="auto" v-model="data.phone"></v-text-field>
          
          

          <v-btn @click="submit" color="primary" class="mt-4">
              <v-icon>mdi-plus</v-icon>
              <span>Submit Form</span>
          </v-btn>

        </v-card>
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
import axios from 'axios'

export default {
  data: function(){
    return {
      data: {
        name: 'saahalla',
        email: 'shl@m.c',
        dob: '09-09-1999',
        address: 'sleman',
        phone: '089998889998'
      },
      rule: [
        value => !!value || 'Required.'
      ],
    }
  },
  mounted() {

  },
  methods: {
    submit: async function(){
      /* data yang akan dikirim ke API create VA */  
      const data = this.data
      console.log(JSON.stringify(data))
      // alert(data)

      await axios({
        method: 'post',
        url: 'http://localhost:3300/forms/create',
        data: data

      }).then(response => {
        const results = response.data;
        if(results.status === true) {
          console.log(results.data)
          this.result = results.data

          this.$router.push('/dashboard/data')
        }else{
          alert('network error')
        }

      }).catch(error => {
          console.log(error)
      })
    }
  }
}
</script>