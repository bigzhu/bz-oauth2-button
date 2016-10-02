<style lang=less>
  .ui.button.oauth {
    margin: 0.75em
  }
  @font-face {font-family: 'douban';
    src: url('./assets/douban.eot'); /* IE9*/
    src: url('./assets/douban.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
    url('./assets/douban.woff') format('woff'), /* chrome、firefox */
    url('./assets/douban.ttf') format('truetype'), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
    url('./assets/douban.svg#douban') format('svg'); /* iOS 4.1- */
  }
  i.icon.douban{
    font-family:"douban" !important;
    font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
  }
  .ui.douban.button {
    background-color: #66AD70;
    color: #fff;
  }
  .ui.douban.button:hover {
    background-color: #499E55;
  }
  i.icon.douban:before {
    content: "\e94a";
  }
  .ui.qq.button {
    color: #fff;
    background-color: #44BADC;
  }
  .ui.qq.button:hover {
    background-color: #35A2C1;
  }
</style>

<template>
  <div>
    <a v-for="oauth in oauths" @click="run($event, oauth)" :href="getHref(oauth)" v-bind:class="'ui ' + oauth + ' button oauth'">
      <i v-bind:class="oauth + ' icon'"></i>
      {{getName(oauth)}}
    </a>
  </div>
</template>

<script>
  export default {
    props: ['oauths', 'url', 'function_name'],
    computed: {
    },
    components: {
    },
    data: function () {
      return {
      }
    },
    methods: {
      upperFirst: function (string) {
        return string.charAt(0).toUpperCase() + string.substring(1).toLowerCase()
      },
      run: function (e, oauth) {
        // show loading
        e.target.className += ' loading '
        if (this.function_name) {
          window[this.function_name]('api_' + oauth)
        }
      },
      getName: function (oauth) {
        if (oauth === 'qq') {
          return 'QQ'
        } else {
          return this.upperFirst(oauth)
        }
      },
      getHref: function (oauth) {
        if (this.function_name) {
          return 'javascript:void(0);'
        }
        if (this.url) {
          return this.url + '/api_' + oauth
        } else {
          return '/api_' + oauth
        }
      }
    }
  }
</script>
