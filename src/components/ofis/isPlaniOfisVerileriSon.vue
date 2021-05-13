<template>
  <div>
    <b-table
      :items="items"
      :fields="fields"

      sort-icon-left
      responsive="sm"
    ></b-table>

    <div>
      Sorting By: <b>{{ sortBy }}</b>, Sort Direction:
      <b>{{ sortDesc ? 'Descending' : 'Ascending' }}</b>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
  export default {
      props : ["item"],
    data() {
      return {
        sortBy: 'il_kodu',
        sortDesc: false,
        fields: [
          { key: 'il_kodu', sortable: true },
          { key: 'numarataj', sortable: true },
          { key: 'geometri', sortable: true },
          { key: 'toplam', sortable: true },
        { key: 'islem', sortable: false }

        ],
        items: [
          { il_kodu: this.item.il_kodu, numarataj: this.item.numarataj, geometri: this.item.geometri, 
          toplam: this.item.toplam_is,
          'islem':'tus gelecek' },
        ]
      }
    }
  }
</script>