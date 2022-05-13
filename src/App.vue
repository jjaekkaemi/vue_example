<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
      <button @click="move()">함수로 페이지 이동하고 데이터 주고 받기</button>
    </div>
    <router-view />
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  watch: {
    //데이터의 변화를 감지하는 기능
    $route(to, from) {
      //router의 변화를 감지함
      console.log("watch router to :", to, "from :", from);
    },
  },
  props: {
    // 상위 component 에게 데이터 전달 받음
    msg: String,
    msg2: Number,
  },
  computed: {
    //실시간으로 데이터 변화를 인식하여 함수 실행
    computed_example() {
      return this.list.slice().reverse();
    },
  },
  created() {},
  mounted() {},
  methods: {
    move() {
      switch (this.$route.name) {
        case "Home":
          this.$router.push({
            name: "About",
            params: { parmas_data: "Hello!" },
          });
          break;
        case "About":
          this.$router.push({ name: "Home", query: { query_data: "Hello2" } });
          break;
      }
    },
  },
  data() {
    return {
      list: ["a", "b", "c"],
      routepage: "",
    };
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
