<template>
  <q-page class="flex flex-center col">
    <div><h4>
          <q-img style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/logo.png" />小測驗</h4></div>
    <div><h4 class="bold green">{{toM(n)}} + {{toM(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="check()" placeholder="你的答案"/></h4></div>
    <div><q-btn size="xl" color = "primary" v-if = "win" @click="reset()">答對了! 按此再來</q-btn></div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      n:4,
      m:3,
      ans: '',
      win: false
    }
  },
  methods: {
    reset() {
      this.win = false;
      this.n = Math.floor(Math.random()*10 + 4);
      this.m = Math.floor(Math.random()*10 + 3);
    },
    check() {
      if (this.fromM(this.ans) == this.n + this.m && this.isM(this.ans)) {
        this.win = true
      }
    },
    isM(t) {
      const list = t.split('');
      var ans = true;
      for (var i = 0; i < list.length; i++) {
         if (list[i] >= 6) {
          ans = false
         }
       }
       return ans
    },
    toM(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num %  6)
        num = Math.floor(num / 6)
      }
      return ans.join('')
    },
    fromM(m) {
      var ans = 0;
      const list = String(m).split('');
      for (var i = list.length - 1; i >= 0; i--) {
        ans += list[i] * 6**(list.length - i - 1)
      }
      return ans
    }
  },
  mounted() {
    this.reset()
  }
}
</script>

<style type="text/css" scoped="">

  .col {
    width: 100%;
    text-align: center;
    flex-direction: column !important;
    justify-content: center;
    align-items: center;
  }
</style>
