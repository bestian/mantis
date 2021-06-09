<template>
  <q-page class="flex flex-center">
    <table>
      <tr>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/logo.png" />
          螳螂人乘法表
        </th>
        <th v-for="i in items" :key="i">
          {{toM(i)}}
        </th>
      </tr>
      <tr v-for="i in items" :key="i">
        <th>
          {{ toM(i) }}
        </th>
        <td v-for="j in items" :key="j" class="bold green">
          {{ toM(i * j) }}
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
      items: [1,2,3,4,5]
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

  td {
    text-align: center;
  }

  th {
    background-color: #eee;
  }
</style>
