<template>
    <div class="search" v-on:mouseenter="focusInput" v-on:mouseleave ="unfoucusInput">
      <i class="icon fas fa-search"/>
      <form v-on:submit.prevent="onSubmit">
          <input type="text" class="input" ref="input" v-model="search"/>
      </form>
      <item  v-for="item in results" v-bind:key="item.id" :post="item" />
    </div>
</template>

<script>
import ResultItem from './ResultItem';

const POST_API = 'https://jsonplaceholder.typicode.com/posts';
export default {
  data: function () {
    return {
      search: '',
      results: [],
    };
  },
  components: {
    item: ResultItem,
  },
  methods: {
    focusInput() {
      console.log('DEBUG');
      this.$refs.input.focus();
    },
    unfoucusInput() {
      this.$refs.input.blur();
      this.results = [];
    },
    onSubmit() {
      fetch(POST_API)
        .then(res => res.json())
        .then(json => json.filter(el => el.title.indexOf(this.search) >= 0))
        .then(results => { this.results = results.splice(0,5); });
    },
  },
};
</script>

<style>
.search {
  max-width: 40px;
  background: #fff;

  padding: 12px;

  border-radius: 5px;
  transition: 500ms ease-in-out;
}

.search:hover {
  max-width: 200px;
}
.icon {
  color: #0663df;
}

.input {
  display: inline-block;
  width: 0px;

  outline: none;

  border: none;
  border-bottom: 1px solod black;
  transition: 450ms ease-in-out;

  caret-color: #76a7f6;
  color: #76a7f6;
}
form {
  display: inline;
}

.search:hover .input {
  width: calc(100% - 22px);
}
</style>
