<template>
  <div>
    <label for="category">Category</label>
    <select name="category" v-model="selectedCategory">
      <option v-for="category in categories" v-bind:value="category.name">
        {{ category.name }}
      </option>
    </select>
    <div v-if="selectedCategory === 'Tech'">
      <label for="tag">Tag</label>
      <select name="tag" v-model="selectedTag">
        <option v-for="tag in tags" v-bind:value="tag.id">
          {{ tag.name }}
        </option>
      </select>
    </div>
    <a class="btn" v-on:click="submit">Button</a>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'name',
  data () {
    return {
      selectedCategory: '',
      selectedTag: '',
      categories: [
        {id: 1, name: 'Tech'},
        {id: 2, name: 'Design'},
        {id: 3, name: 'Report'},
      ],
      tags: []
    }
  },
  methods: {
    submit: function() {
      axios.get('/api/tasks').then((response) => {
      }, (error) => {
          this.$router.push('/about')
      });
    }
  }
}
</script>

<style scoped lang="scss">
</style>
