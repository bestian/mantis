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
    <table>
      <tr>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/spider.png" />
          蜘蛛人乘法表
        </th>
        <th v-for="i in items2" :key="i">
          {{toS(i)}}
        </th>
      </tr>
      <tr v-for="i in items2" :key="i">
        <th>
          {{ toS(i) }}
        </th>
        <td v-for="j in items2" :key="j" class="bold brown">
          {{ toS(i * j) }}
        </td>
      </tr>
    </table>
    <table>
      <tr>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/frog.png" />
          青蛙人乘法表
        </th>
        <th v-for="i in items3" :key="i">
          {{toF(i)}}
        </th>
      </tr>
      <tr v-for="i in items3" :key="i">
        <th>
          {{ toF(i) }}
        </th>
        <td v-for="j in items3" :key="j" class="bold blue">
          {{ toF(i * j) }}
        </td>
      </tr>
    </table>
    <table>
      <tr>
        <th>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/binary.png" />
          二進制乘法表
        </th>
        <th v-for="i in items4" :key="i">
          {{toB(i)}}
        </th>
      </tr>
      <tr v-for="i in items4" :key="i">
        <th>
          {{ toB(i) }}
        </th>
        <td v-for="j in items4" :key="j" class="bold gold">
          {{ toB(i * j) }}
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
      items: [1,2,3,4,5],
      items2: [1,2,3,4,5,6,7],
      items3: [1,2,3],
      items4: [1,2,3,4,5]
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
    },
    toS(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num %  8)
        num = Math.floor(num / 8)
      }
      return ans.join('')
    },
    toF(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 4)
        num = Math.floor(num / 4)
      }
      return ans.join('')
    },
    toB(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 2)
        num = Math.floor(num / 2)
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

  th:first-child, td:first-child {
    width: 180px;
  }
</style>
