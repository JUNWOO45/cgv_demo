<template>
  <div>
    <router-link to="/">돌아가기</router-link>
    <h1>상세내용</h1>
    <div class="information">
      <p class="title">{{movie.name}}</p>
      <p class="director">감독 : {{movie.director}}</p>
    </div>
  </div>
</template>

<script>
  export default {
    created: function() {
      var id = this.$route.params.id
      this.$http.get(`/api/movies/${id}`)
      .then((response) => {
        this.movie = response.data[0]
        console.log("response: ", response);
      })
    },
    data: function() {
      return {
        movie : {}
      }
    }
  }
</script>