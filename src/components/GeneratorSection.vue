<template>
  <div class="radiowrap">
    <label for="random">
      <input
        checked="true"
        @click="filterMode = 'random'"
        name="category"
        type="radio"
        id="random"
      />Random</label
    >
    <label for="family">
      <input
        @click="filterMode = 'family'"
        name="category"
        type="radio"
        id="family"
      />Family</label
    >
    <label for="office"
      ><input
        @click="filterMode = 'office'"
        name="category"
        type="radio"
        id="office"
      />Office</label
    >
    <label for="children"
      ><input
        @click="filterMode = 'children'"
        name="category"
        type="radio"
        id="children"
      />Children</label
    >
  </div>
  <button @click="getExcuse()">IM SO SORRY</button>
  <p>
    <q>{{ this.excuseData[0].excuse }}</q>
  </p>
</template>

<script>
const url = "https://excuser.herokuapp.com/v1/excuse";
export default {
  name: "GeneratorSection",
  props: {},
  data() {
    return {
      excuseData: [],
      filterMode: "random",
    };
  },
  computed: {
    filterUrl() {
      let filteredUrl = "";
      if (this.filterMode === "random") {
        filteredUrl = url;
      } else if (this.filterMode === "family") {
        filteredUrl = url + "/family";
      } else if (this.filterMode === "office") {
        filteredUrl = url + "/office";
      } else if (this.filterMode === "children") {
        filteredUrl = url + "/children";
      }
      return filteredUrl;
    },
  },
  methods: {
    async getExcuse() {
      const response = await fetch(this.filterUrl);

      this.excuseData = await response.json();
      console.log(this.filterMode, this.excuseData[0].category);
    },
  },
  async created() {
    const response = await fetch(url);
    this.excuseData = await response.json();
  },
};
</script>

<style scoped>
.radiowrap {
  padding: 32px;
}
p {
  padding: 20px;
}
button {
  all: unset;

  padding: 4px;
  border-radius: 4px;
  font-weight: bolder;
  background: rgb(38, 187, 236);
  box-shadow: 2px 4px black;
  transition: 0.2s ease;
}
button:hover {
  transform: scale(1.02);
  box-shadow: 4px 8px grey;
}
button:active {
  transform: scale(0.9);
  box-shadow: 1px 2px black;
}
</style>
