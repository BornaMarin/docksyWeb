<template>
  <div class="flex flex-column justify-center align-center p-24">
    <div>
      <v-img class="rounded-full" height="100px" width="100px" src="/Capture.JPG"/>
    </div>
    <span class="p-8">
      Author name: "{{authorName}}"
    </span>
    <span class="p-8">
      About the author:
    </span>
    <span>
      "{{authorText}}"
    </span>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        authorName: '',
        authorText: ''
      }
    },
    async created() {
      let url = 'https://student-sport-results.herokuapp.com/api/metas/get'
      const res = await this.$axios.get(url)
      console.log(res.data)
      this.authorText = res.data.authorDescription
      this.authorName = res.data.author
    }
  }
</script>
