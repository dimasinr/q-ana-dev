<template>
    <q-page>
        <div class="row">
            <q-table
                title="Table"
                :rows="uwsgi"
                :columns="columns"
                row-key="name"
                class="col">
            </q-table>
        </div>

    </q-page>
</template>

<script>
// import { ref } from 'vue'

export default {
  data () {
    return {
      columns: [
        { name: 'No', label: 'No', field: 'No', align: 'center', sortable: true },
        { name: 'Nama', label: 'Nama', field: 'Nama', align: 'center', sortable: true },
        { name: 'Email', label: 'Email', field: 'Email', align: 'center', sortable: true },
        { name: 'No_Telfon', label: 'Nomor Telefon', field: 'No_Telfon', align: 'left', sortable: true },
        { name: 'Beauty_Bar', label: 'Beauty Bar', field: 'Beauty_Bar', align: 'center', sortable: true },
        { name: 'Treatment', label: 'Treatment', field: 'Treatment', align: 'center', sortable: true },
        { name: 'Ip_Address', label: 'Ip Address', field: 'Ip_Address', align: 'left', sortable: true }
      ],
      uwsgi: []
    }
  },
  methods: {
    getUwsgi () {
      this.$axios.get('http://192.168.123.119:2000/uwsgi-api.php')
        .then((res) => {
          this.uwsgi = res.data
          console.log(res.data)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  // filter: ref(''),
  mounted () {
    this.getUwsgi()
  }
}
</script>
