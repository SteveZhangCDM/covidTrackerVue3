<template>
  <main v-if="!loading">
    <data-title :text="text" :dataDate="dataDate" />
    <data-boxes :stats="stats" />
    <country-select :countries="countries" @get-country="getCountryData" />
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-grey-500 text-3xl mt-10 mb-6">FetchingData</div>
    <img :src="loadingImg" class="w-24 m-auto" alt="" />
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '@/components/DataTitle.vue';
import DataBoxes from '@/components/DataBoxes.vue';
import CountrySelect from '@/components/CountrySelect.vue';

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,

      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],

      /* eslint-disable global-require */

      loadingImg: require('../../public/loading.gif'),

      /* eslint-enable global-require */
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.stats = country;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    console.log(data);

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
