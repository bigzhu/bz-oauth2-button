<template>
  <div>
    <doc :name="name"
      :desc="desc"
      :parm_desc="parm_desc"
      :parms="parms"
      :code="code"
      >
      <bz :oauths="oauths"></bz>
    </doc>
  </div>
</template>

<script>
  import Bz from './Bz.vue'
  import Doc from 'bz-doc'
  export default {
    components: {
      Bz,
      Doc
    },
    data: function () {
      return {
        oauths: [
          'vk',
          'douban',
          'youtube',
          'facebook',
          'google plus',
          'twitter',
          'github',
          'instagram'
        ],
        name: 'bz-oauth2-button',
        desc: '生成 Oauth2 按钮',
        parms: [
          {parm: 'oauths', desc: '一个list, 指定要显示的oauth方式:' + `['vk', 'twitter']`}
        ],
        code: '<oauth2 :oauths="oauths"></oauth2>'
      }
    },
    methods: {
      run: function () {
        window.alert('用不着运行，这货是直接运行的')
      }
    }
  }
</script>

<style>
</style>
