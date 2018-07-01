<template>
  <recycle-list class="list" for="(item, index) in longList" switch="type" @loadmore="loadmore">
    <cell-slot case="product">
      <floor :product="item" />
    </cell-slot>
  </recycle-list>
</template>

<script>
import Card from "./Card.vue";
import Floor from "./Floor.vue";

const dataset = {
  floor: [
    {
      type: "floor",
      title: "就造专属感，给孩子寻个座椅好玩伴",
      desc:
        "犹记得儿时的风筝带着斑斓的色彩在天空飘过；那小河里躲迷藏的鱼虾，还待着小伙伴们一起去捕捉，如今的孩童没有了这些简单且纯粹的娱乐项目，生活在高楼城市中的他们，该当怎样度过自己的童年才是美好的？",
      pictures: [
        "https://gw.alicdn.com/tfscom/i3/48292642/TB29OtIakz_F1JjSZFkXXcCaXXa_!!48292642.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i4/706778912/TB2hvwSXBvBIuJjy1zeXXbGBpXa_!!706778912-0-beehive-scenes.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i3/706778912/TB2wX.fcxz9F1JjSZFsXXaCGVXa_!!706778912-0-beehive-scenes.jpg_250x250q90s200.jpg"
      ],
      count: 237
    },
    {
      type: "floor",
      title: "睡袍穿不对，脱光也不媚！",
      desc:
        "“Ihatemynightgown（我讨厌我的睡袍）.”经典电影《罗马假日》中，赫本饰演的安妮公主躺在梦幻的宫廷大床上，抱怨她身上那华丽的大睡袍臃肿不便，为公主的浪漫逃逸埋下伏笔。想象一下，男朋友刚刚",
      pictures: [
        "https://gw.alicdn.com/imgextra/i3/3044653839/TB2a_nAXgsSMeJjSspdXXXZ4pXa_!!3044653839-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i1/3044653839/TB2qrPCXiERMeJjSspiXXbZLFXa_!!3044653839-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i1/3044653839/TB2ySjuXgsSMeJjSspeXXa77VXa_!!3044653839-0-beehive-scenes.jpg_250x250q90s200.jpg"
      ],
      count: 876
    },
    {
      type: "floor",
      title: "上天入海？运动相机帮你搞定",
      desc:
        "现如今相机好像成为了我们每个人必不可少的装备，不管是专业的相机还是我们可拍照的手机，我们使用到它的频率也越来越高。为了追求更好的拍摄质量，人们似乎也愿意花更多的钱去购买好的拍摄装备",
      pictures: [
        "https://gw.alicdn.com/tfscom/i3/462856946/TB2VzQswB4lpuFjy1zjXXcAKpXa_!!462856946.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/tfscom/i2/2811920170/TB2rCqHpVXXXXcZXpXXXXXXXXXX_!!2811920170.png_250x250.jpg",
        "https://gw.alicdn.com/imgextra/i4/836552381/TB2c1q3aZSfF1JjSsplXXbrKFXa_!!836552381-0-beehive-scenes.jpg_250x250q90s200.jpg"
      ],
      count: 59
    },
    {
      type: "floor",
      title: "关于培根的那些事，教你吃得门清",
      desc:
        "培根一直被认为是早餐的头盘，早上烤两片面包，平底锅煎一片培根、一个鸡蛋，和生菜一起夹在面包中，有荤有素，就是一顿丰富美味的西式早餐。培根的英文名是“Bacon”，原意是烟熏的猪肋条肉，或烟熏背脊肉",
      pictures: [
        "https://gw.alicdn.com/imgextra/i2/603964020/TB24zFbarwTMeJjSszfXXXbtFXa_!!603964020-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i2/603964020/TB2txtdarsTMeJjy1zcXXXAgXXa_!!603964020-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/tfscom/i3/1635378022/TB2plKDbFXXXXaTXpXXXXXXXXXX-1635378022.jpg_250x250q90s200.jpg"
      ],
      count: 3576
    },
    {
      type: "floor",
      title: "轻奢风来袭，皮艺床打造典雅居室",
      desc:
        "对于追求生活高品质感的小伙伴来说，皮艺家具是展现其高格调的途径之一。想要营造出奢华质感的卧室环境，大气庄重的皮床当然是不错的选择。特别是简欧风或是美式古典风格的家居环境，如果配以皮艺床简直就是点睛之笔",
      pictures: [
        "https://gw.alicdn.com/imgextra/i2/787557947/TB2erNKawoQMeJjy0FoXXcShVXa_!!787557947-0-beehive-scenes.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i1/787557947/TB2KANyaBUSMeJjy1zkXXaWmpXa_!!787557947-0-beehive-scenes.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i3/787557947/TB2lwdGayERMeJjy0FcXXc7opXa_!!787557947-0-beehive-scenes.jpg_250x250q90s200.jpg"
      ],
      count: 36
    },
    {
      type: "floor",
      title: "提高品质生活，从用好水开始",
      desc:
        "我们生活中每天都要喝水、用水，可是你真的喝到、用到好水了么？为了得到更高品质的生活，我们需要更多的好东西让我们的生活更有档次，那不如就从改变你每天都要亲密接触的水开始吧",
      pictures: [
        "https://gw.alicdn.com/imgextra/i2/1904229646/TB2dRg4dgoQMeJjy0FpXXcTxpXa_!!1904229646-2-daren.png_250x250.jpg",
        "https://gw.alicdn.com/imgextra/i1/1904229646/TB2JtOjfOAKL1JjSZFoXXagCFXa_!!1904229646-2-daren.png_250x250.jpg",
        "https://gw.alicdn.com/imgextra/i1/1904229646/TB2BSXjdwsSMeJjSspeXXa77VXa_!!1904229646-2-daren.png_250x250.jpg"
      ],
      count: 74
    },
    {
      type: "floor",
      title: "酒鬼到了意大利，收不住的红酒心",
      desc:
        "意大利是一个集古典与艺术于一身的国度，这里是艺术的发源地之一，也是欧洲最早种植葡萄的国家之一。意大利的酿酒历史超过4000年，本地葡萄品种过千不止，古希腊人称其为“葡萄酒之国”",
      pictures: [
        "https://gw.alicdn.com/imgextra/i1/2872639756/TB21lwtXjihSKJjy0FiXXcuiFXa_!!2872639756-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i1/2872639756/TB2zgRJdwMPMeJjy1XdXXasrXXa_!!2872639756-0-daren.jpg_250x250q90s200.jpg",
        "https://gw.alicdn.com/imgextra/i2/2872639756/TB2Ki0NdBUSMeJjSspfXXX0VFXa_!!2872639756-0-daren.jpg_250x250q90s200.jpg"
      ],
      count: 182
    }
  ],
  card: [
    {
      type: "card",
      poster:
        "http://gw.alicdn.com/tps/i4/1611893164/TB2t4mtXJqUQKJjSZFIXXcOkFXa_!!0-juitemmedia.jpg_320x320q80s150.jpg",
      title: "澳洲牛排10份装送刀叉酱料黄油",
      subtitle1: "送平底锅前3000仅78",
      subtitle2: "私厨经典 镇店套餐",
      got: 173,
      progress: 35,
      price: { real: 108, sale: 240.0 }
    },
    {
      type: "card",
      poster:
        "http://gw.alicdn.com/tps/i2/2838892713/TB2ma39aqmgSKJjSsphXXcy1VXa_!!0-juitemmedia.jpg_320x320q80s150.jpg",
      title: "HUAWEI P10",
      subtitle1: "买赠好礼6期免息",
      subtitle2: "6期免息",
      got: 996,
      progress: 89,
      price: { real: 3488, sale: 3488.0 }
    },
    {
      type: "card",
      poster:
        "http://gw.alicdn.com/tps/i3/902257410/TB2pzypfU3IL1JjSZFMXXajrFXa_!!0-juitemmedia.jpg_320x320q80s150.jpg",
      title: "海宁真皮皮衣男绵羊皮夹克外套",
      subtitle1: "店内领券下单438",
      subtitle2: "限送500双皮手套",
      got: 296,
      progress: 16,
      price: { real: 538, sale: 3080.0 }
    },
    {
      type: "card",
      poster:
        "https://gw.alicdn.com/tps/i4/0/TB2Mx3Jg4TI8KJjSspiXXbM4FXa_!!0-juitemmedia.jpg_320x320q80s150.jpg",
      title: "玛丽黛佳元气风动三色腮红正品",
      subtitle1: "满108领券立减10元",
      subtitle2: "宛若天生粉红好气色",
      got: 1457,
      progress: 61,
      price: { real: 49, sale: 69.8 }
    },
    {
      type: "card",
      poster:
        "https://gw.alicdn.com/tps/i2/0/TB2i25DgN6I8KJjSszfXXaZVXXa_!!0-juitemmedia.jpg_320x320q80s150.jpg",
      title: "王小二高山脐橙，酸甜如初恋",
      subtitle1: "前3分钟半价",
      subtitle2: "VC仓库，酸甜如初恋",
      got: 598,
      progress: 42,
      price: { real: 29.8, sale: 56.1 }
    }
  ]
};

const modal = weex.requireModule("modal");
const stream = weex.requireModule("stream");
export default {
  components: { Card, Floor },
  data() {
    return {
      longList: [],
      pageNo: 1
    };
  },
  methods: {
    fetchData() {
      stream.fetch(
        {
          method: "GET",
          type: "json",
          url: `/newretail/main/shoplist?lng=116.302413&lat=40.0373118&city_id=3&address=&channel=supermarket&device_id=AD0D131CD1984C5F83CCEF5D16E577B8%7C1515657553041&scene_id=0&scene_type=shop&rn=20&pn=${
            this.pageNo
          }&user_type=default&fromalipay=0&type=1`
        },
        res => {
          if (res.ok) {
            let result = res.data.result.shop_list;
            let newData = result.map((item, i) => {
              let shopInfo = item.shop_info;
              let cards = item.display_window;
              let pics = cards.map(card => {
                let matches = card.image.match(/(jpeg|png)$/);
                let format = matches && matches.length > 0 ? matches[1] : "";
                return {
                  src:
                    "https://fuss10.elemecdn.com/" + card.image + "." + format,
                  name: card.name,
                  price: card.current_price
                };
              });
              return {
                type: "product",
                title: shopInfo.brand_name,
                logo: shopInfo.logo_url,
                desc: shopInfo.shop_name,
                rate: shopInfo.overall_rating,
                month: shopInfo.saled_month,
                takeOutPrice: shopInfo.takeout_price,
                takeout_cost: shopInfo.takeout_cost,
                distance: shopInfo.distance,
                deliveryTime: shopInfo.delivery_time,
                pictures: pics
              };
            });
            this.longList = this.longList.concat(newData);
          } else {
            modal.alert({
              message: "请求错误",
              okTitle: "确定"
            });
          }
        }
      );
    },
    loadmore() {
      this.pageNo += 1;
      this.fetchData();
    }
  },
  mounted() {
    this.fetchData();
  }
};
</script>

<style scoped>
.list {
  width: 750px;
  background-color: #efefef;
}
.banner-image {
  width: 750px;
  height: 235px;
}
</style>
