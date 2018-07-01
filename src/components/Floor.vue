<template recyclable>
  <div class="product">
    <div class="product-title-box row">
      <image class="product-logo" :src="product.logo"/>
      <div>
        <text class="product-title">{{product.desc}}</text>
        <div class="row">
          <text class="product-desc" lines="2">{{product.rate}}分</text>
           <text class="product-desc" lines="2">月销{{product.month}}</text>
        </div>
        <div class="row">
          <text class="product-fee">¥{{product.takeOutPrice}}起送</text>
          <text class="product-fee">配送费¥{{product.takeout_cost}}</text>
          <text class="product-fee">{{product.distance}}Km | </text>
          <text class="product-fee" lines="2">{{product.deliveryTime}}分</text>
        </div>
      </div>
    </div>
    <div class="product-image-box row">
      <div class="product-image-out" v-for="(source, x) in product.pictures" :key="x">
        <image class="product-image" :src="source.src"/>
        <text>{{source.name}}</text>
        <text>{{source.price}}</text>
      </div>
    </div>
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
.product-title-box {
  flex-direction: row;
  margin-top: 20px;
  align-content: top;
  padding: 30px;
}
.product-logo {
  width: 160px;
  height: 160px;
}
.product-title {
  font-size: 40px;
  text-align: center;
  padding-left: 30px;
}
.product-desc {
  lines: 2;
  color: #999;
  font-size: 30px;
  padding-left: 30px;
  padding-right: 30px;
}
.product-fee {
  lines: 2;
  color: #999;
  font-size: 30px;
  padding-left: 10px;
  padding-right: 10px;
}
.product-image-box {
  flex-direction: row;
  justify-content: space-between;
  margin-top: 20px;
}
.product-image-out {
  padding: 30px;
}
.product-image {
  width: 180px;
  height: 180px;
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
