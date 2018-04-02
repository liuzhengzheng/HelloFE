<template>
  <div class="wrapper">
    <i-row v-for="(item, index) in res" :key="index" :gutter="10">
      <div :id="item.code" class="res-name"><h2>{{item.name}}</h2></div>
      <i-col v-for="(itemdata, indexkey) in item.data" :key="indexkey" :xs="8" :sm="6" :md="4">
        <i-card :bordered="false">
          <a :href="itemdata[0]" target="_blank">{{ indexkey }}</a>
          <div class="detail">{{ itemdata[1] }}</div>
        </i-card>
      </i-col>
    </i-row>
    <i-backtop :height="100" :bottom="200">
      <div class="top">返回顶端</div>
    </i-backtop>
  </div>
</template>

<script>
import { Card, Row, Col, BackTop } from 'iview'
import { Resources } from '@/assets/data/sdata.js'
export default {
  data () {
    return {
      res: Resources
    }
  },
  components: {
    'i-card': Card,
    'i-row': Row,
    'i-col': Col,
    'i-backtop': BackTop
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper{
  padding-bottom: 20px;
}
.ivu-row{
  margin-top: 30px;
}
.ivu-col{
  margin-top: 10px;
}
.res-name h2{
  margin-left: 8px;
  background-color: #57a3f3;
  width: 140px;
  color: #fff;
  padding: 10px 20px;
}
.ivu-card{
  height: 90px;
}
.ivu-card a{
  width: 100%;
  display: inline-block;
  font-weight: bold;
  color: #57a3f3;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.ivu-card .detail{
  height: 37px;
  overflow: hidden;
  color: #aaa;
  font-size: 12px;
  font-weight: 500;
}
.top{
  padding: 10px;
  background: rgba(0, 153, 229, .7);
  color: #fff;
  text-align: center;
  border-radius: 2px;
}
</style>
