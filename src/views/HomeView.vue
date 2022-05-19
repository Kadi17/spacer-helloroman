<template>
  <div class="wrapper">
    <Claim/>
    <Searchinput/>
  </div>
</template>
<script>

import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim-one.vue';
import Searchinput from '@/components/Searchinput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  // eslint-disable-next-line vue/no-unused-components
  components: { Claim, Searchinput },
  name: 'HomeView',
  data() {
    return {
      searchValues: '',
      results: [],
    };
  },

  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function () {
      axios.get(`${API}?q=${this.searchValues}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>
<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 30px;
  height: 100vh;
  width: 100%;
  justify-content: center;
  background-image: url('../assets/heroimage.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0%;
}

</style>
