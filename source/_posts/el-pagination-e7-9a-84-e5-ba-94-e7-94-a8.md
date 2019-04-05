---
title: el-pagination的应用
url: 38.html
id: 38
categories:
  - 未分类
date: 2018-11-08 22:19:45
tags:
---

最近项目用到了elementUI，其中用到分页功能的时候使用el-pagination组件，傻不拉几的认为把数据直接堆到el-pagination上面就能自动给分页的，结果写了后发现没效果。研究了一下发现分页数据还是需要自己来分的。获取数据后，设置page-size每页显示条数，total设置总的数据条数，页码就会自动分好。然后利用el-pagination的current-change事件，这个事件会在页码切换时触发，接收当前页面作为参数，利用这个事件实现分页。简单记录一下 代码如下：

<template>
  <div>
    <ul>
      <li v-for="item in currentPage">{ {item}}</li>
    </ul>
    <el-pagination
      :page-size="5"
      :total="pageData.length"
      background
      @current-change="pageChange"
      ></el-pagination>
  </div>
</template>
<script>
export default {
  data () {
    return {
      fileList: [],
// 所有数据
      pageData: [
        '第1条',
        '第2条',
        '第3条',
        '第4条',
        '第5条',
        '第6条',
        '第7条',
        '第8条',
        '第9条',
        '第10条',
        '第11条',
        '第12条',
        '第13条',
        '第14条',
        '第15条',
        '第16条',
        '第17条',
        '第18条',
        '第19条',
        '第20条',
        '第21条',
        '第22条',
        '第23条',
        '第24条',
        '第25条'
      ],
// 当前页面显示数据
      currentPage: []
    }
  },
// 挂载后取前五条作为第一页数据
  mounted () {
    this.currentPage = this.pageData.slice(0, 5)
  },
  methods: {
// 每次页面切换更新currentPage数据
    pageChange (page) {
      console.log(page)
      this.currentPage = this.pageData.slice((page - 1) * 5, page * 5)
    }
  },
}
</script>