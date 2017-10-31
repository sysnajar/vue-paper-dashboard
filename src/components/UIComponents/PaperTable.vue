<template>
  <div>
    <div class="header">
      <slot name="header">
        <h4 class="title">{{title}}</h4>
        <p class="category">{{subTitle}}</p>
      </slot>
    </div>
    <div class="content table-responsive table-full-width">
      <table class="table" :class="tableClass">
        <thead>
          <th v-for="column in columns">
				{{earkColumn(column)}}
         </th>
        </thead>
        <tbody>
          <tr v-for="item in data">
            <td v-for="column,c in columns" v-if="hasValue(item, column)">
				
					<span v-if="column=='f1' || column=='f2'">
							<img v-bind:src="'http://creden.co/face/images/'+itemValue(item, column)" width="100">
					</span>
					<span v-else>
					        <span v-if="column=='isIdentical' && item[column]=='false'">
 							     <font color='red'>{{itemValue(item, column)}}</font>
					       </span>
						   <span v-else>
 							     {{itemValue(item, column)}}
						   </span>
					</span>
				
           </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
  export default {
    props: {
      columns: Array,
      data: Array,
      type: {
        type: String, // striped | hover
        default: 'striped'
      },
      title: {
        type: String,
        default: ''
      },
      subTitle: {
        type: String,
        default: ''

      }
    },
    created: function () {
      window.t = this
    },
    computed: {
      tableClass () {
        return `table-${this.type}`
      }
    },
    methods: {
      hasValue (item, column) {
        return item[column.toLowerCase()] !== 'undefined'
      },
      itemValue (item, column) {
        var ret = item[column]
        if (column === 'isIdentical' && ret === 'true') ret = 'Yes'
        if (column === 'isIdentical' && ret === 'false') ret = 'No'
        if (column === 'confidence' && ret) ret = parseFloat(ret * 100).toFixed(2) + '%'
        return ret
      },
      earkColumn (column) {
        console.log(column)
        if (column === 'f1') return 'Photo1'
        if (column === 'f2') return 'Photo2'
        if (column === 'isIdentical') return 'Match?'
        return column
      }
    }
  }

</script>
<style>

</style>
