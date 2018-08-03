<template>
   <div class="center" v-if="list">
      <div class="basics"
        v-for="(item, index) in list" v-bind:key="index">
          <div class="basics-left"  :class="{'cannotuse': index > showLavel}">
              <img :src="item.url" alt="">
          </div>
          <div class="basics-right" >
              <div class="detail" :class="{'done': detail.done, 'complete': detail.complete, 'cannotuse': index > showLavel}" 
                v-for="(detail, i) in item.detail" v-bind:key="i" @click="showDetail((index <= showLavel || list[index-1].done), detail, index)">
                  <div class="top" :class="{'active': index <= showLavel && myDetail.firstname === detail.firstname && myDetail.lastname === detail.lastname}">
                      <img :src="detail.url" alt="">
                  </div>
                  <div class="bottom">
                      <div class="detail">
                          <img src="/static/images/png/baseline_category_white_48dp.png" alt="">
                          <div class="number">{{checkedTrueLength(detail.recommend)}}/{{detail.recommend && detail.recommend.length}}
                          </div>
                      </div>
                      <div class="detail">
                          <img src="/static/images/png/sharp_filter_tilt_shift_white_18dp.png" alt="">
                          <div class="number">{{checkedTrueLength(detail.optional)}}/{{detail.optional && detail.optional.length}}</div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  props: ["list", "showLavel"],
  name: "Center",
  data() {
    return {
      myDetail: this.list[0].detail[0]
    };
  },
  methods: {
    isCategory(category) {
      return this.list.findIndex(item => item == category) != -1;
    },
    checkedLength(detail) {
      return detail.length;
    },
    checkedTrueLength(detail) {
      return detail.filter(item => item.checked == true).length;
    },
    showDetail(canclick, item, listIndex) {
      if (canclick) {
        this.myDetail = item;
        this.$emit("showDetail", { detail: this.myDetail, list: listIndex });
      }
    }
  }
};
</script>

