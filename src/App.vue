<template>
  
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <img :src="logo"> -->
    <ul>
      <li v-for="(item, index) of stories" :key="index">
        {{item.title}}
        <img :src="item.images[0]">
        </li>

    </ul>
  </div>
</template>

<script>
export default {
  data(){
    return {
      stories:[],
      // logo:require('./assets/logo.png')
    }
  },
  created() {
    
    // this.logo = require('./assets/logo.png');

    //   var api = 'https://news-at.zhihu.com/api/4/news/latest'
    this.axios.get('news/latest').then(response=> {
      var stories = response.data.stories;
      for (const key in stories) {
        // window.console.log(stories)
        stories[key]['images'][0].replace(/pic3/g, "pic1")
        window.console.log(stories[key]['images'][0])
      }
      this.stories = stories
    })
  },
}
</script>

