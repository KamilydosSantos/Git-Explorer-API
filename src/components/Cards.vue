<template>
  <div class="card-content">
    <img src="../assets/union.png" alt="foto usuario" />
    <div>
      <h3>{{ repositories.name }}</h3>
      <p>Descrição do repo</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cards",
  props: {
    repositories: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card-content {
  display: flex;
  align-items: center;
  background-color: #fff;
  height: 84px;
  max-width: 960px;
  margin: 12px auto 0 auto;
  padding-left: 12px;
  border-radius: 5px;
  // img {
  //   grid-column: 1/2;
  // }
  div {
    margin: 0 0 0 12px;
    text-align: left;
    grid-column: 2/3;
  }
  h3 {
    font: normal 700 16px "Arial";
    margin: 0;
  }
  p {
    font: normal 400 12px "Arial";
    margin: 0;
  }
}
</style>