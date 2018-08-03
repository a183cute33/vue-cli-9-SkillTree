<template>
  <div class="main">
    <div class="left">
        <div class="title">FRONT-END SKILL TREE</div>
        <div class="current">CURRENT RANK</div>
        <div class="noob">
            <div class="top">FRONT-END</div>
            <div class="bottom">{{lavel[showLavel].title}}</div>
            <div class="img">
                <img :src="lavel[showLavel].url" alt="">
            </div>
            <div class="note">
                <div class="text" v-html="lavel[showLavel].text">
                </div>
            </div>
        </div>
    </div>
    <div class="right">
        <center :showLavel='showLavel' :list='list' @showDetail='showDetail'></center>
        <right :myDetail='myDetail'></right>
    </div>
  </div>
</template>
<script>
import center from "./center.vue";
import right from "./right.vue";
export default {
  components: { center, right },
  name: "Main",
  data() {
    return {
      list: [
        {
          name: "Basics",
          url: "/static/images/img-planet-basics@2x.png",
          done: false,
          detail: [
            {
              firstname: "BASIC",
              lastname: "SKILLS",
              url: "/static/images/png/baseline_category_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "Learn HTML", checked: true },
                { title: "Basics of CSS", checked: false },
                { title: "Basics of JavaScript", checked: false }
              ],
              optional: []
            },
            {
              firstname: "BASIC",
              lastname: "TOOLS",
              url: "/static/images/png/baseline_build_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "Git - Version Contro", checked: false },
                { title: "Basic Terminal Usage", checked: false },
                { title: "Text Editor", checked: false },
                { title: "Heart of Reserching", checked: false }
              ],
              optional: []
            }
          ]
        },
        {
          name: "CSS",
          url: "/static/images/img-planet-css@2x.png",
          done: false,
          detail: [
            {
              firstname: "CSS",
              lastname: "FRAMEWORK",
              url: "/static/images/png/baseline_flip_to_front_white_48dp.png",
              done: false,
              complete: false,
              recommend: [{ title: "Bootstrap", checked: false }],
              optional: [
                { title: "UIKit", checked: false },
                { title: "Foundation", checked: false },
                { title: "Semantic UI", checked: false }
              ]
            },
            {
              firstname: "CSS",
              lastname: "PREPROCESSORS",
              url: "/static/images/png/baseline_view_quilt_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "Sass", checked: false },
                { title: "PostCSS", checked: false }
              ],
              optional: [
                { title: "Less", checked: false },
                { title: "Stylus", checked: false }
              ]
            },
            {
              firstname: "CSS",
              lastname: "ARCHITECHTURE",
              url: "/static/images/png/baseline_developer_board_white_48dp.png",
              done: false,
              complete: false,
              recommend: [{ title: "OOCSS", checked: false }],
              optional: [
                { title: "SMACSS", checked: false },
                { title: "BEM", checked: false }
              ]
            },
            {
              firstname: "CSS",
              lastname: "SKILLS",
              url: "/static/images/png/baseline_devices_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "Responsive", checked: false },
                { title: "Flexbox", checked: false }
              ],
              optional: []
            },
            {
              firstname: "CSS",
              lastname: "MASTERY",
              url: "/static/images/png/baseline_widgets_white_48dp.png",
              done: true,
              complete: false,
              recommend: [],
              optional: [
                { title: "Grid Layout", checked: false },
                { title: "Animation", checked: false },
                { title: "Transform 2D, 3D", checked: false }
              ]
            }
          ]
        },
        {
          name: "JavaScript",
          url: "/static/images/img-planet-js@2x.png",
          done: false,
          detail: [
            {
              firstname: "BASIC",
              lastname: "DOM",
              url: "/static/images/png/baseline_hdr_strong_white_48dp.png",
              done: true,
              complete: false,
              recommend: [],
              optional: [{ title: "jQuery", checked: false }]
            },
            {
              firstname: "WEB",
              lastname: "DRAWING",
              url: "/static/images/png/baseline_gradient_white_48dp.png",
              done: true,
              complete: false,
              recommend: [],
              optional: [
                { title: "SVG", checked: false },
                { title: "Canvas", checked: false },
                { title: "D3.js", checked: false }
              ]
            },
            {
              firstname: "JAVASCRIPT",
              lastname: "SKILLS",
              url: "/static/images/png/baseline_format_quote_white_48dp.png",
              done: false,
              complete: false,
              recommend: [{ title: "ES6", checked: false }],
              optional: []
            },
            {
              firstname: "JAVASCRIPT",
              lastname: "FRAMEWORK",
              url: "/static/images/png/baseline_developer_mode_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "Vue.js", checked: false },
                { title: "Angular", checked: false },
                { title: "React.js", checked: false }
              ],
              optional: []
            },
            {
              firstname: "JAVASCRIPT",
              lastname: "PREPROCESSORS",
              url: "/static/images/png/baseline_nfc_white_48dp.png",
              done: true,
              complete: false,
              recommend: [],
              optional: [
                { title: "TypeScript", checked: false },
                { title: "Babel", checked: false },
                { title: "CoffeeScript", checked: false }
              ]
            }
          ]
        },
        {
          name: "Managers",
          url: "/static/images/img-planet-managers@2x.png",
          done: false,
          detail: [
            {
              firstname: "PACKAGE",
              lastname: "MANAGERS",
              url: "/static/images/png/baseline_device_hub_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "NPM", checked: false },
                { title: "YARN", checked: false }
              ],
              optional: [{ title: "Bower", checked: false }]
            },
            {
              firstname: "TASK",
              lastname: "RUNNERS",
              url: "/static/images/png/baseline_import_contacts_white_48dp.png",
              done: false,
              complete: false,
              recommend: [
                { title: "npm scripts", checked: false },
                { title: "gulp", checked: false }
              ],
              optional: [{ title: "grunt", checked: false }]
            },
            {
              firstname: "BUILD",
              lastname: "TOOLS",
              url: "/static/images/png/baseline_table_chart_white_48dp.png",
              done: false,
              complete: false,
              recommend: [{ title: "Webpack", checked: false }],
              optional: [{ title: "Parcel", checked: false }]
            }
          ]
        }
      ],
      lavel: [
        {
          title: "Noob",
          url: "/static/images/img-ship-noob@2x.png",
          text: `<div class="white">Welcome aboard. Your mission is: </div>
                        <div class="red">Collect the resources and learn the skills to upgrade the ship. </div>
                        <div class="white">Good luck, captain! </div>`
        },
        {
          title: "Beginner",
          url: "/static/images/img-ship-beginner@2x.png",
          text: `<div class="white">Congradulations! You become the </div>
                        <div class="red">“Front-end Beginnner”. </div>
                        <div class="white">Keep searching the resources to upgrade to the next level. </div>`
        },
        {
          title: "Developer",
          url: "/static/images/img-ship-developer@2x.png",
          text: `<div class="white">You’re doing well! Now you’re a  </div>
                        <div class="red">“Front-end Developer”. </div>
                        <div class="white">It’s close to complete the upgrading program. </div>
                        </br>
                        <div class="white">Next level: Front-end Master. </div>`
        },
        {
          title: "Master",
          url: "/static/images/img-ship-master@2x.png",
          text: `<div class="white">Excellent! You’re a </div>
                        <div class="red">“Front-end Master” </div>
                        <div class="white">now. But a new galary was just detected by the system. </div>
                         </br>
                        <div class="white">Captain, make your choice. </div>`
        }
      ],
      myDetail: null,
      showLavel: 0
    };
  },
  watch: {
    list: {
      handler: function(val, oldVal) {
        val.map(m => {
          let checkedAll = [];
          m.detail.map(p => {
            let com = p.recommend.every(list => list.checked == true);
            let opt = p.optional.every(list => list.checked == true);
            if (com && opt) p.complete = true;
            if (com) {
              p.done = true;
              checkedAll.push(true);
            } else {
              checkedAll.push(false);
            }
          });
          m.done = checkedAll.every(list => list == true);
        });
      },
      deep: true
    }
  },
  mounted() {
    this.myDetail = this.list[0].detail[0];
  },
  methods: {
    showDetail(detail) {
      this.myDetail = detail.detail;
      this.showLavel = detail.list;
    }
  }
};
</script>