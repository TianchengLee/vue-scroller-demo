<template>
  <scroller class="hello" ref="sc" :on-refresh="refresh" :on-infinite="infinite">
    <!-- content goes here -->
    <ul>
      <li v-for="item in datas" :key="item">{{ item }}</li>
    </ul>
  </scroller>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      datas: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    };
  },
  methods: {
    refresh(done) {
      setTimeout(() => {
        // console.log(this)
        this.datas = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        done();
      }, 1500);
    },
    infinite(done) {
      setTimeout(() => {
        // console.log(this)
        // this.bottom = this.bottom + 10
        // done();
        for (let i = this.datas.length + 1, j = 0; j < 10; j++, i++) {
          this.datas.push(i);
        }

        this.$refs.sc.finishInfinite(this.datas.length === 40);
      }, 1500);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
li {
  margin: 10px 10px;
  border: 1px solid #000;
  height: 30px;
  line-height: 30px;
}
a {
  color: #42b983;
}
</style>
