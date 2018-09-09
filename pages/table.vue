<template>
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
        <td class="text-xs-lelt">{{ props.item.s_name }}</td>
        <td class="text-xs-lelt">{{ props.item.s_class }}</td>
        <td class="text-xs-lelt">{{ props.item.s_group }}</td>
      </template>
    </v-data-table>
    <div>
      <v-btn color="success">รับออเดอร์</v-btn>
      <v-btn color="error">ชำระเงิน</v-btn>
     
    
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "รหัสสินค้า",
          align: "left",
          sortable: false,
          value: "name"
        },
        { text: "รายการเครื่องดื่ม", value: "calories" },
        { text: "ราคา(เย็น)", value: "calories" },
        { text: "ราคา(ร้อน)", value: "fat" },
        
        
        
      ],
      desserts: []
    };
  },
  async created() {
    this.getstudent();
  },
  methods: {
    async getstudent() {
      let res = await this.$http.get(
      "http://127.0.0.1/php-api/list-student.php"   
      );
      this.desserts = res.data.student;
    }
  }
};
</script>