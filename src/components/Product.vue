<template recyclable>
  <div class="product">
    <text class="product-title">{{product.title}}</text>
    <text class="product-desc" lines="2">{{product.desc}}</text>
    <div class="product-image-box row">
      <image class="product-image" :src="source" v-for="(source, x) in product.pictures" :key="x" />
    </div>
    <text class="product-comment" v-if="product.count">{{product.count}} 人说好</text>
  </div>
</template>

<script>
export default {
  props: ["product"]
};
</script>

<style scoped>
.row {
  flex-direction: row;
}
.product {
  margin-bottom: 15px;
  background-color: #fff;
}
.product-title {
  font-size: 40px;
  text-align: center;
  padding-top: 35px;
  padding-bottom: 25px;
}
.product-desc {
  lines: 2;
  color: #999;
  font-size: 30px;
  padding-left: 30px;
  padding-right: 30px;
}
.product-image-box {
  flex-direction: row;
  justify-content: space-between;
  margin-top: 20px;
}
.product-image {
  width: 245px;
  height: 245px;
}
.product-comment {
  color: #52bfe6;
  font-size: 32px;
  text-align: right;
  padding-right: 50px;
  margin-top: 25px;
  margin-bottom: 20px;
}
</style>
