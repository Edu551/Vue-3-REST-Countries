<template>
  <div>
    <h1 class="text-center">Select a continent</h1>
    <div
      class="btn-group mb-4 col-lg-12"
      role="group"
      aria-label="Basic example"
    >
      <button
        @click="(e) => filterBy('Americas')"
        type="button"
        class="btn btn-primary"
      >
        Americas
      </button>
      <button
        @click="(e) => filterBy('Asia')"
        type="button"
        class="btn btn-primary"
      >
        Asia
      </button>
      <button
        @click="(e) => filterBy('Africa')"
        type="button"
        class="btn btn-primary"
      >
        Africa
      </button>
      <button
        @click="(e) => filterBy('Europe')"
        type="button"
        class="btn btn-primary"
      >
        Europe
      </button>
      <button
        @click="(e) => filterBy('Oceania')"
        type="button"
        class="btn btn-primary"
      >
        Oceania
      </button>
      <button
        @click="(e) => filterBy('Polar')"
        type="button"
        class="btn btn-primary"
      >
        Polar
      </button>
    </div>

    <div class="table-overflow">
      <table class="table table-hover text-center">
        <thead>
          <tr>
            <th scope="col">Continent</th>
            <th scope="col">Country</th>
            <th scope="col">Capital</th>
            <th scope="col">Population</th>
          </tr>
        </thead>
        <tbody v-for="pais of filteredCountries" :key="pais.id">
          <tr>
            <td>{{ pais.region }}</td>
            <td>{{ pais.name }}</td>
            <td>{{ pais.capital }}</td>
            <td>{{ pais.population }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Countries from "../services/countries";

export default {
  name: "CountriesView",
  data() {
    return {
      allCountries: [],
      arrayCountries: [],
    };
  },
  mounted() {
    Countries.listar().then((coutryList) => {
      this.allCountries = coutryList.data;
      this.arrayCountries = coutryList.data;
    });
  },
  computed: {
    filteredCountries() {
      return this.arrayCountries.map((item) => item);
    },
  },
  created() {
    // this.getCountries();
    this.filterBy();
  },
  methods: {
    filterBy(region) {
      return !region
        ? (this.arrayCountries = this.allCountries)
        : (this.arrayCountries = this.allCountries.filter(
            (country) => country.region === region
          ));
    },
    //   getCountries() {
    //     axios
    //       .get(
    //         "https://restcountries.com/v2/all?fields=name,capital,region,population"
    //       )
    //       .then((coutryList) => {
    //         console.log(coutryList.data);
    //         this.allCountries = coutryList.data;
    //       })
    //       .catch((e) => {
    //         console.log(e);
    //       });
    //   },
  },
};
</script>

<style scoped>
.table-overflow {
  max-height: 21rem;
  overflow-y: auto;
}
th {
  position: sticky;
  top: 0;
  z-index: 2;
  background: #fff;
  box-shadow: 0 1px 0 0 #ddd, 0 -5px 0 0 #fff;
}
</style>
