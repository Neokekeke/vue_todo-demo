<template>
  <div id="app">


    <!-- 背景图片的遮罩层 -->
    <div id="cover"></div>

    <!-- header组件 -->
    <Header></Header>

    <!-- todo组件 -->
    <TODO></TODO>

    <!-- footer组件 -->
    <Footer></Footer>

  </div>
</template>

<script>
import Header from './components/header.vue'
import Footer from './components/footer.vue'
import TODO from './components/todo.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    TODO,
  },
  data(){
    return {
      text : 'aaaaaa'
    }
  },
  methods: {

  }
}
</script>

<style>
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
a {
  color: inherit;
  text-decoration: none;
}
body {
  background: rgb(240, 242, 245);
  font-family: "Helvetica Neue",Helvetica,Arial,"Hiragino Sans GB","Hiragino Sans GB W3","Microsoft YaHei UI","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
  font-size: 14px;
  color: #444;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  width: 100%;
  height: 1080px;
  background: url('./assets/bg.jpg') center center no-repeat;
  position: relative;
  z-index: 1;
}

/* 这里是遮罩层 */
#cover{
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #999999;
  opacity: 0.5;
  z-index: -1;
}

</style>
