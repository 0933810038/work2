<template>
<v-app>
   <v-form v-model="valid">
    <h1>Search Member</h1>
    <v-text-field
      v-model="member"
    ></v-text-field>
  </v-form>
  <div class="text-xs-center">
     <v-btn round color="primary" dark @click="Dologin"><v-icon>contacts</v-icon></v-btn>
  </div>

   <div>
    <v-data-table
      :headers="headers"
      :items="desserts"
      class="elevation-1"
    >
      <template slot="headerCell" slot-scope="props">
        <v-tooltip bottom>
          <span slot="activator">
            {{ props.header.text }}
          </span>
          <span>
            {{ props.header.text }}
          </span>
        </v-tooltip>
      </template>
      <template slot="items" slot-scope="props">
        <td>{{ props.item.s_code }}</td>
        
      </template>
    </v-data-table>

  </div>
  </v-app>

  </template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'Member',
          align: 'left',
          sortable: false,
          value: 'name',
        },
        
        
       
      ],
      desserts: [],
    }
  },
async created() {
    //เรียกใช้งาน
    this.getstudent()
  }, 
methods: {
    async Dosearch() {
      let res = await this.$http.post('http://127.0.0.1/php-api/search1.php',{
           member : this.member,
      })
      if (res.data.ok){
          this.$router.push('')
      }
    },
}
}
</script>