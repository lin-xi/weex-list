<template>
  <list class="listPage" @loadmore="fetchData" loadmoreoffset="10">
    <cell v-for="(color, i) in lists" :key="i" class="cell">
      <div class="panel" :style=" 'background-color: ' + color">
        <text class="text" :style=" 'color:' + reverseColor(color) ">{{color}}</text>
      </div>
    </cell>
  </list>
</template>

<script>
const modal = weex.requireModule("modal");
export default {
  data() {
    let l = [];
    for (let i = 0; i < 10000; i++) {
      l.push(this.randomColors());
    }
    return {
      lists: l
    };
  },
  methods: {
    fetchData(event) {
      modal.toast({
        message: "fetchData",
        duration: 1
      });

      fetch(
        "/restapi/shopping/v3/restaurants?latitude=39.9622909&longitude=116.4015559&offset=0&limit=8&extras[]=activities&extras[]=tags&extra_filters=home&rank_id=&terminal=h5"
      )
        .then(function(response) {
          return response.json();
        })
        .then(function(data) {
          console.log(data);
        });
    },
    randomColors() {
      let c = Math.floor(Math.random() * 16777215)
        .toString(16)
        .toUpperCase();
      return "#" + "000000".substr(0, 6 - c.length) + c;
    },
    reverseColor(color) {
      let r = color.substr(1, 2);
      let g = color.substr(3, 2);
      let b = color.substr(5, 2);
      return `rgb(${255 - parseInt(r, 16)}, ${255 - parseInt(g, 16)}, ${255 -
        parseInt(b, 16)})`;
    }
  }
};
</script>

<style scoped>
.panel {
  width: 750px;
  height: 250px;
  margin-top: 10px;
  margin-bottom: 10px;
  flex-direction: column;
  justify-content: center;
  border-width: 2px;
  border-style: solid;
  border-color: rgb(162, 217, 192);
  background-color: rgba(162, 217, 192, 0.2);
}

.text {
  font-size: 100px;
  text-align: center;
  color: #41b883;
}
</style>