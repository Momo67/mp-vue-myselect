<template id="test" lang="html">
  <div id="my-select">
    <my-select ref="mystatut"
      id="sel-statut"
      v-model="arbre.statut"
      :multiple="multiple"
      trackby="Id"
      fieldname="Data"
      sort="asc"
      :placeholder="placeholder"
      :options="options"
    ></my-select>
    <my-select
      v-model="arbre.genre"
      :src="src_url"
      item="Genre"
      sort="asc"
      placeholder="Sélectionner un genre"
      :delay="500"
    ></my-select>
    <code>Arbre: {{arbre}}</code><br/>
    <code>Statut: {{arbre.statut}}</code><br />
    <button @click="setValues">Set</button>
  </div>
</template>

<script>
import MySelect from './MySelect'

export default {
  name: 'test',
  components: {
    MySelect
  },
  data () {
    return {
      statut: null,
      options: [
        {Id: 9, Data: 'A surveiller', SortOrder: 70, IsActive: 1},
        {Id: 6, Data: 'En attente d\'abattage', SortOrder: 40, IsActive: 1},
        {Id: 7, Data: 'En attente de remplacement', SortOrder: 50, IsActive: 1},
        {Id: 5, Data: 'En attente de soins', SortOrder: 30, IsActive: 1},
        {Id: 8, Data: 'En attente de tomographie', SortOrder: 60, IsActive: 1},
        {Id: 10, Data: 'En demande d\'abattage', SortOrder: 39, IsActive: 1},
        {Id: 1, Data: 'Existant', SortOrder: 10, IsActive: 1},
        {Id: 2, Data: 'Supprimé', SortOrder: 20, IsActive: 1}
      ],
      arbre: {
        statut: 9,
        genre: 17,
        cadastre: 1
      },
      placeholder: 'Status Quo',
      multiple: false,
      src_url: 'http://localhost/goeland/objet/ajax/arbre_get_select.php'
    }
  },
  methods: {
    onMySelectEvent: function () {
      alert('Appel de onMySelectEvent, event: ' + event.button)
    },
    setValues () {
      this.arbre.statut = 5
      this.arbre.genre = 10
    }
  },
  mounted () {
    this.arbre.statut = [{value: -1, label: '- Tous -', order: 1}]

    if (this.multiple) {
      this.arbre.statut = [{value: -1, label: '-Tous-'}]
    } else {
      this.arbre.statut = 1
    }
    this.arbre.genre = 19
  }
}
</script>

<style lang="css">
</style>
