<template>
    <div class="row">


      <div class="col-md-12">
        <div class="card">
          <paper-table :title="table1.title" :sub-title="table1.subTitle" :data="table1.data" :columns="table1.columns">

          </paper-table>
        </div>
      </div>

       

    </div>
</template>
<script>
  import PaperTable from 'components/UIComponents/PaperTable.vue'
  const tableColumns = ['id', 'f1', 'f2', 'isIdentical', 'confidence']
  const tableData = [{
    id: 1,
    name: 'Dakota Rice',
    confidence: '0.5954',
    f1: 'https://creden.co/face/images/f1_5.png',
    f2: 'https://creden.co/face/images/f2_5.png',
    isIdentical: 'true'
  },
  {
    id: 2,
    name: 'Minerva Hooper',
    salary: '$23,789',
    country: 'Curaçao',
    isIdentical: 'false',
    confidence: '0.3954',
    f1: 'https://creden.co/face/images/f1_5.png',
    f2: 'https://creden.co/face/images/f2_5.png'
  },
  {
    id: 3,
    name: 'Sage Rodriguez',
    salary: '$56,142',
    country: 'Netherlands',
    city: 'Baileux'
  },
  {
    id: 4,
    name: 'Philip Chaney',
    salary: '$38,735',
    country: 'Korea, South',
    city: 'Overland Park'
  },
  {
    id: 5,
    name: 'Doris Greene',
    salary: '$63,542',
    country: 'Malawi',
    city: 'Feldkirchen in Kärnten'
  }]
  window.table = tableData

  export default {
    components: {
      PaperTable
    },
    data () {
      return {
        table1: {
          title: 'Photo List',
          subTitle: 'Here\'re sample data',
          columns: [...tableColumns],
          data: [...tableData]
        }
      }
    },
    mounted () {
      load()
    }
  }

</script>
<style>

</style>
