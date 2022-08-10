<template>
  <h1><slot /></h1>
  <p>
    If you are in need of an excuse, just choose the category and click the
    button!
  </p>
  <GeneratorSection></GeneratorSection>
</template>

<script>
import GeneratorSection from "@/components/GeneratorSection.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: { GeneratorSection },
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
