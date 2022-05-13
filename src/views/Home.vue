<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>[Home.vue] Query Data : {{ $route.query.query_data }}</h1>
    <HelloWorld msg="[HelloWorld.vue] " :msg2="msg_data" />
    <HelloWorld2 @emit-example="emit_example" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import HelloWorld2 from "@/components/HelloWorld2.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
    HelloWorld2,
  },

  methods: {
    emit_example(data) {
      this.msg_data += data;
    },
  },
  data() {
    return {
      msg_data: 0,
    };
  },
};
</script>
