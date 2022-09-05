<template>
  <div class="block">
    <h3>You took {{ score }}ms</h3>
    <p>{{ rank }}</p>
  </div>
</template>

<script>
  export default{
    props: ['score'],
    data() {
      return{
        rank: null
      }
    },
    mounted() {
      if(this.score < 250){
        this.rank = 'Blazing fast'
      }else if (this.score < 400) {
        this.rank = 'Kinda fast'
      } else {
        this.rank = 'Not so fast'
      }
    }
  }

</script>

<style>
  .block{
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    color: #fff;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>