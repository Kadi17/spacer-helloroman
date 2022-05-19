<template>
  <div class="searchWrapper">
        <input
          id="search"
          name="search"
          v-model="searchValues"
          @input="handleInput"
        />
    </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Searchinput',
};
</script>
<style lang="scss" scoped>
.searchWrapper {
    margin-top: 50px;
  display: flex;
  flex-direction: column;
  width: 250px;

  label{
    font-family: 'Montserrat', sans-serif;
  }

  input {
    height: 30px;
    border: 0;
    background: none;
    border-bottom: 1px solid black;
  }
}
</style>
