  <template>
  <div class="wrap">
    <ul id="marquee">
      <li v-for="(item,index) in lists" :key="index">{{item}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'Scroller',
  props: {
    lists: Array
  },
  // props: ['lists'], // 父组件传入数据， 数组形式
  methods: {
    move () {
      // 获取内容区宽度
      const width = document.getElementById('marquee').scrollWidth
      const marquee = document.getElementById('marquee')
      let speed = width // 位移距离
      // 设置位移
      setInterval(function () {
        speed = speed - 3
        // 如果位移超过文字宽度，则回到起点
        if (-speed >= width) {
          speed = width
        }
        marquee.style.transform = 'translateX(' + speed + 'px)'
      }, 40)
    }
  },
  mounted () {
    this.move()
  }
}
</script>
 <style scoped>
/*样式*/
.wrap {
  overflow: hidden;
  color: #FF0101;
}
#box {
  height: 100%;
}
ul,
li {
  margin: 0;
  padding: 0;
}
ul {
  white-space: nowrap;
  margin: 0 10px;
}
li {
  height: 100%;
  list-style: none;
  margin-right: 10px;
  display: inline-block;
}
</style>
