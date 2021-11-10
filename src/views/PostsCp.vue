<template>
<div class="post-wrapper">
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th>번호</th>
        <th>제목</th>
        <th>내용</th>
      </tr>
    </thead>
    <tbody>
    <tr v-for=" v in posts" :key="v.id" >
      <th>{{v.id}}</th>
        <th>{{v.title}}</th>
        <th>{{v.body}}</th>
    </tr>
    </tbody>
  </table>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Posts',
  data () {
    return {
      posts: []
    }
  },
  async created () {
    const url = 'https://jsonplaceholder.typicode.com/posts'
    const { data } = await axios.get(url)
    this.posts = data
    console.log(this.posts)
  }
}
</script>

<style lang="scss" scoped>
 .post-wrapper {
   width: 90%;
   max-width: 720px;
   margin: 2em auto;
   overflow-y :auto;
 }
</style>
