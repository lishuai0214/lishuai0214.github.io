<style scoped>
    .layout{
        border: 1px solid #d7dde4;
        background: #f5f7f9;
        position: relative;
        border-radius: 4px;
        overflow: hidden;
    }
    .layout-header-bar{
        background: #fff;
        box-shadow: 0 1px 1px rgba(0,0,0,.1);
        width: 60px;
    }
    .layout-logo-left{
        width: 90%;
        height: 30px;
        background: #5b6270;
        border-radius: 3px;
        margin: 15px auto;
    }
    .menu-icon{
        transition: all .3s;
    }
    .rotate-icon{
        transform: rotate(-90deg);
    }
    .menu-item span{
        display: inline-block;
        overflow: hidden;
        width: 69px;
        text-overflow: ellipsis;
        white-space: nowrap;
        vertical-align: bottom;
        transition: width .2s ease .2s;
    }
    .menu-item i{
        transform: translateX(0px);
        transition: font-size .2s ease, transform .2s ease;
        vertical-align: middle;
        font-size: 16px;
    }
    .collapsed-menu span{
        width: 0px;
        transition: width .2s ease;
    }
    .collapsed-menu i{
        transform: translateX(5px);
        transition: font-size .2s ease .2s, transform .2s ease .2s;
        vertical-align: middle;
        font-size: 22px;
    }
    .markdown-body {
      box-sizing: border-box;
      width: 980px;
      margin: 30px auto 0 auto;
      padding: 45px;
      font-size: 16px;
      background: #ffffff;
    }

    @media (max-width: 767px) {
      .markdown-body {
        padding: 15px;
      }
    }
</style>
<template>
    <div class="layout">
        <Layout :style="{height: `${pageHeight}px`}">
            <Sider :collapsed-width="78" v-model="isCollapsed" style="overflow: auto;">
                <Menu active-name="1-1" theme="dark" width="auto" :class="menuitemClasses" @on-select="onmenuselect">
                    <Submenu name="1">
                        <template slot="title">
                            <Icon type="ios-navigate"></Icon>
                            道氏理论
                        </template>
                        <MenuItem name="1-1">1、道氏理论-技术分析的鼻祖</MenuItem>
                        <MenuItem name="1-2">2、道氏理论的形成过程</MenuItem>
                        <MenuItem name="1-3">3、道氏理论的三个假设五个定理</MenuItem>
                        <MenuItem name="1-4">4、定理1：道氏理论的三种趋势</MenuItem>
                        <MenuItem name="1-5">5、定理2：主要走势(空头或多头市场)</MenuItem>
                        <MenuItem name="1-6">6、定理3：主要的空头市场</MenuItem>
                        <MenuItem name="1-7">7、定理4：主要的多头市场</MenuItem>
                        <MenuItem name="1-8">8、定理5：次级折返走势</MenuItem>
                        <MenuItem name="1-9">9、道氏理论基本观点：一 浪潮、波浪及涟漪</MenuItem>
                        <MenuItem name="1-10">10、道氏理论基本观点：二 基本趋势的几个阶段</MenuItem>
                        <MenuItem name="1-11">11、道氏理论基本观点：三 相互验证的原则</MenuItem>
                        <MenuItem name="1-12">12、道氏理论的缺陷</MenuItem>
                        <MenuItem name="1-13">13、道氏理论总结</MenuItem>
                    </Submenu>
                    <Submenu name="2">
                        <template slot="title">
                            <Icon type="ios-keypad"></Icon>
                            亚当理论
                        </template>
                        <MenuItem name="2-1">1、亚当理论-序</MenuItem>
                        <MenuItem name="2-2">2、第一章：亚当理论为何</MenuItem>
                        <MenuItem name="2-3">3、第二章：神话故事</MenuItem>
                        <MenuItem name="2-4">4、第三章：要在市场中成功，我们应该</MenuItem>
                        <MenuItem name="2-5">5、第四章：从事操作不需要懂得太多</MenuItem>
                        <MenuItem name="2-6">5、第五章：市场中什么事情最重要</MenuItem>
                        <MenuItem name="2-7">7、第六章：是与应该</MenuItem>
                        <MenuItem name="2-8">8、第七章：避免武断</MenuItem>
                        <MenuItem name="2-9">9、第八章：操作系统</MenuItem>
                        <MenuItem name="2-10">10、第九章：市场中什么最重要</MenuItem>
                        <MenuItem name="2-11">11、第十章：何谓趋势</MenuItem>
                        <MenuItem name="2-12">12、亚当理论第十一章：一再重复的最基本形式是什么样子</MenuItem>
                        <MenuItem name="2-13">13、亚当理论第十二章：准确的重复会产生什么情形</MenuItem>
                        <MenuItem name="2-14">14、亚当理论第十三章：什么事会造成最完美的对称</MenuItem>
                        <MenuItem name="2-15">15、亚当理论第十四章：预判第二映像</MenuItem>
                        <MenuItem name="2-16">16、亚当理论第十五章：用简单的方法画出第二映像图</MenuItem>
                    </Submenu>
                    <Submenu name="3">
                        <template slot="title">
                            <Icon type="ios-analytics"></Icon>
                            TEST
                        </template>
                        <MenuItem name="3-1">test1</MenuItem>
                        <MenuItem name="3-2">test2</MenuItem>
                    </Submenu>
                </Menu>
            </Sider>
            <Layout>
              <div v-html="markdown2html" v-highlight class="markdown-body"></div>
            </Layout>
        </Layout>
    </div>
</template>

<script>
    import axios from 'axios'
    import marked from 'marked'
    import showdown from 'showdown'
    export default {
        data () {
            return {
                isCollapsed: false,
                pageHeight: 900,
                markdown2html: null
            }
        },
        created() {
          this.setpageHeight()
          this.getMarkdownfile(`/mddocs/stocks/daoshililun/1.md`)
        },
        computed: {
            menuitemClasses () {
                return [
                    'menu-item',
                    this.isCollapsed ? 'collapsed-menu' : ''
                ]
            }
        },
        methods: {
          onmenuselect(data){
            const num = data.split("-")
            switch (num[0]) {
              case "1":
                this.getMarkdownfile(`/mddocs/stocks/daoshililun/${num[1]}.md`)
                break;
              case "2":
                this.getMarkdownfile(`/mddocs/stocks/yadanglilun/${num[1]}.md`)
                break;
              default:
                break;
            }
          },
          setpageHeight () {
            this.pageHeight = window.innerHeight - 2
            window.onresize = () => {
                return (() => {
                    this.pageHeight = window.innerHeight - 2
                })()
            }
          },
          getMarkdownfile(url){
            let self = this
            self.markdown2html = null
            //const converter = new showdown.Converter()
            axios.get(url)
              .then(function (response) {
                //self.markdown2html = converter.makeHtml(response.data)
                self.markdown2html = marked(response.data)
              })
              .catch(function (error) {
                console.log(error);
              });
          }
      }
  }
</script>
