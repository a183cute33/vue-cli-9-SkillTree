<template>
    <div class="right" v-if="myDetail">
        <div class="top">
            <div class="img">
                <img :src="myDetail.url" alt="">
            </div>
            <div class="text">
                <span>{{myDetail.firstname}}</span>
                <span>{{myDetail.lastname}}</span>
            </div>
        </div>
        <div class="bottom">
            <div class="main">
                <div class="recomended" v-if="myDetail.recommend.length>0">
                    <div class="img">
                        <img src="/static/images/png/baseline_settings_white_48dp.png" alt="">
                    </div>
                    <div class="title">
                        <span>
                            RECOMMENDED</span>
                    </div>
                    <ul  v-for="(rec, index) in myDetail.recommend" v-bind:key="index">
                        <li :class="{'active': rec.checked && rec.checked}" @click="clickChecked(rec)">{{rec.title}}</li>
                    </ul>
                </div>
                    <div class="optional" v-if="myDetail.optional.length>0">
                    <div class="img">
                        <img src="/static/images/png/baseline_filter_tilt_shift_white_48dp.png" alt="">
                    </div>
                    <div class="title">
                        <span>
                            OPTIONAL</span>
                    </div>
                    <ul v-for="(opt, index) in myDetail.optional" v-bind:key="index">
                        <li :class="{'active': opt.checked && opt.checked}" @click="clickChecked(opt)">{{opt.title}}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  name: "Right",
  props: ["myDetail"],
  methods:{
      clickChecked(option){
          option.checked = true;
      }
  },
};
</script>

