<template>
  <div class="wrapper" ref="aaaa">
    <div>
      <!--1.无论是否设置click:false, button都可以点击-->
      <button @click="btnClick">按钮</button>
      <!--2.必须设置click:true, 那么div才能监听点击-->
      <div @click="divClick">呵呵呵呵</div>
      <ul class="content">
        <li>分类列表1</li>
        <li>分类列表2</li>
        <li>分类列表3</li>
        <li>分类列表4</li>
        <li>分类列表5</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'Category',
  data () {
    return {
      scroll: null
    }
  },
  // 组件创建完后调用
  mounted () {
    this.scroll = new BScroll(this.$refs.aaaa, {
      // probeType: 3,
      // pullUpLoad: true
    })
    this.scroll.on('scroll', (position) => {
      console.log(position)
    })
    this.scroll.on('pullingUp', () => {
      console.log('向上拉可以加载更多内容')
    })
  },
  methods: {
    btnClick () {
      console.log('你触发了btnClick事件')
    },
    divClick () {
      console.log('你触发了divClick事件')
    }
  }
}
</script>

<style scoped>
  .wrapper {
    height: 150px;
    background-color: skyblue;
    overflow: hidden;
    /*overflow-y: scroll;*/
  }
</style>
