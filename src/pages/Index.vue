<template>
  <q-page class="flex flex-center">
    <table>
      <tr>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/pi.png" />
          人類數學
        </th>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/logo.png" />
          螳螂人數學  
        </th>
      </tr>
      <tr v-for="i in items" :key="i">
        <td>
          {{i }}
        </td>
        <td class="bold green">
          {{ toM(i) }}
        </td>
      </tr>
    </table>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      items: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25]
    }
  },
  methods: {
    toM(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num %  6)
        num = Math.floor(num / 6)
      }
      return ans.join('')
    }
  }
}
</script>

<style type="text/css" scoped="">
  table {
    font-family: Arial, Helvetica, sans-serif;
    border-collapse: collapse;
    width: 100%;
  }

  table td, table th {  
    border: 1px solid #ddd;
    padding: 8px;
  }

  table tr:nth-child(odd) td {
    background-color: #eee;
  }

  td {
    text-align: center;
  }

</style>
