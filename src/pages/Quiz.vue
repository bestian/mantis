<template>
  <q-page class="flex flex-center col">
    <div><h4>
          <q-img v-if = "type == 'm'" style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/logo.png" />
          <q-img v-if = "type == 's'" style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/spider.png" />
          <q-img v-if = "type == 'f'" style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/frog.png" />
          <q-img v-if = "type == 'b'" style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/binary.png" />
          <q-img v-if = "type == 'r'" style="height: 100px" 
          contain
          src="https://bestian.github.io/mantis/ring.png" />小測驗</h4></div>
    <div v-if = "type=='m'"><h4 class="bold green">{{toM(n)}} + {{toM(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="checkM()" placeholder="你的答案"/></h4></div>

    <div v-if = "type=='s'"><h4 class="bold brown">{{toS(n)}} + {{toS(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="checkS()" placeholder="你的答案"/></h4></div>

    <div v-if = "type=='f'"><h4 class="bold blue">{{toF(n)}} + {{toF(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="checkF()" placeholder="你的答案"/></h4></div>

    <div v-if = "type=='b'"><h4 class="bold gold">{{toB(n)}} + {{toB(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="checkB()" placeholder="你的答案"/></h4></div>

    <div v-if = "type=='r'"><h4 class="bold red">{{toR(n)}} + {{toR(m)}} = ?<q-input type="text" name="ans" v-model="ans" @input="checkR()" placeholder="你的答案"/></h4></div>

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
      win: false,
      type: 'r'
    }
  },
  methods: {
    reset() {
      this.ans = null;
      this.win = false;
//      this.type = ['m','s','f','b','r'][Math.floor(Math.random()*5)];
      this.n = Math.floor(Math.random()*10 + 4);
      this.m = Math.floor(Math.random()*10 + 3);
    },
    checkM() {
      if (this.fromM(this.ans) == this.n + this.m && this.isM(this.ans)) {
        this.win = true
      }
    },
    checkS() {
      if (this.fromS(this.ans) == this.n + this.m && this.isS(this.ans)) {
        this.win = true
      }
    },
    checkF() {
      if (this.fromF(this.ans) == this.n + this.m && this.isF(this.ans)) {
        this.win = true
      }
    },
    checkB() {
      if (this.fromB(this.ans) == this.n + this.m && this.isB(this.ans)) {
        this.win = true
      }
    },
    checkR() {
      if (this.fromR(this.ans) == this.fromR(this.toR(this.n + this.m)) && this.isR(this.ans)) {
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
    isS(t) {
      const list = t.split('');
      var ans = true;
      for (var i = 0; i < list.length; i++) {
         if (list[i] >= 8) {
          ans = false
         }
       }
       return ans
    },
    isF(t) {
      const list = t.split('');
      var ans = true;
      for (var i = 0; i < list.length; i++) {
         if (list[i] >= 4) {
          ans = false
         }
       }
       return ans
    },
    isB(t) {
      const list = t.split('');
      var ans = true;
      for (var i = 0; i < list.length; i++) {
         if (list[i] >= 2) {
          ans = false
         }
       }
       return ans
    },
    isR(t) {
      const list = t.split('');
      var ans = true;
      for (var i = 0; i < list.length; i++) {
         if (list[i] >= 7) {
          ans = false
         }
       }
       return ans
    },
    toM(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 6)
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
    },
    toS(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 8)
        num = Math.floor(num / 8)
      }
      return ans.join('')
    },
    fromS(m) {
      var ans = 0;
      const list = String(m).split('');
      for (var i = list.length - 1; i >= 0; i--) {
        ans += list[i] * 8**(list.length - i - 1)
      }
      return ans
    },
    toF(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 4)
        num = Math.floor(num / 4)
      }
      return ans.join('')
    },
    fromF(m) {
      var ans = 0;
      const list = String(m).split('');
      for (var i = list.length - 1; i >= 0; i--) {
        ans += list[i] * 4**(list.length - i - 1)
      }
      return ans
    },
    toB(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 2)
        num = Math.floor(num / 2)
      }
      return ans.join('')
    },
    fromB(m) {
      var ans = 0;
      const list = String(m).split('');
      for (var i = list.length - 1; i >= 0; i--) {
        ans += list[i] * 2**(list.length - i - 1)
      }
      return ans
    },
    toR(num) {
      var ans = []
      while (num > 0) {
        ans.unshift(num % 7)
        num = Math.floor(num / 7)
      }
      return ans[ans.length-1]
    },
    fromR(m) {
      var ans = 0;
      const list = String(m).split('');
      for (var i = list.length - 1; i >= 0; i--) {
        ans += list[i] * 7**(list.length - i - 1)
      }
      return ans
    },
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
