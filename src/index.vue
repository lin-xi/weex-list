<template>
  <div class="wrapper">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      logo: "https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png"
    };
  }
};
</script>

<style scoped>
.wrapper {
  background-color: #f5f5f5;
}
</style>
