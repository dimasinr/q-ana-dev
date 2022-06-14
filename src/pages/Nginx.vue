<template>
  <div class="q-pa-md">
    <q-table
      title="Table Data"
      :rows="nginxs"
      :columns="columns"
      row-key="name"
      :filter="filter"
    >
      <template v-slot:top-right>
        <q-input borderless dense debounce="300" v-model="filter" placeholder="Search">
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template>
    </q-table>
  </div>
</template>

<script>
import { ref } from 'vue'

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
      nginxs: [],
      filter: ref('')
    }
  },
  methods: {
    getNginxs () {
      this.$axios.get('https://analisdatacus.000webhostapp.com/ana.php')
        .then((res) => {
          this.nginxs = res.data
          console.log(res.data)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted () {
    this.getNginxs()
  }
}
</script>
