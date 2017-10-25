<template>
  <div class="app-main">
    Demo Page Usage
    <simple-demo
      v-for="item in list"
      v-bind:todo="item"
      v-bind:key="item.id">
    </simple-demo>
  </div>
</template>

<script>
import request from '../utils/request'
import SimpleDemo from '../components/SimpleDemo'

export default {
  name: 'demo-page-view',
  components: {SimpleDemo},
  data() {
    return {
      list: [
        { id: 0, text: '蔬菜' },
        { id: 1, text: '奶酪' },
        { id: 2, text: '随便其他什么人吃的东西' }
      ]
    }
  },
  methods: {
    fetch(id, start=0) {
      request
        .get(`/api/proxy/douban_m_rexxvar/v2/user/${id}/following?start=${start}&count=100&ck=76rJ&for_mobile=1`)
        .end((err, {body})=>{
        })
    }
  },
  watch: {
    '$route'(to, from) {
    }
  },
  mounted() {
    const pId = this.$route.params.id
    this.fetch(pId)
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
