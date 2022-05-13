<template>
  <div class="hello">
    <h1>[HelloWorld2.vue]</h1>
    <button @click="button_example()">push!</button>
    <div v-for="(data, idx) in computed_example" :key="idx">
      <div v-if="data == 'e'" style="color: red">{{ data }}</div>
      <div v-else style="color: black">{{ data }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
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
    button_example() {
      this.$emit("emit-example", 1);
      this.list.push("e");
    },
  },
  data() {
    return {
      list: ["a", "b", "c"],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
