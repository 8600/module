
```html
<template>
  <div id="app">
    <slider
    ref="test_prev_next"
    :pagination-visible="true"
    :slides="slides"
    :repeating="true"
    :auto="5000"
    @slide-change-start="onSlideChangeStart"
    @slide-change-end="onSlideChangeEnd"
    @slide-revert-start="onSlideRevertStart"
    @slide-revert-end="onSlideRevertEnd"
    @slider-move="onSliderMove">

    <div v-for="(slide,index) in slides" :key="index">
      <a :href="slide.value">
        <img height="200" :src="slide.image" />
      </a>
    </div>
  </slider>
  <button @click="prependSlide()">插入图片(前)</button>
  <button @click="appendSlide()">插入图片(后)</button>
  <button @click="prev()">上一张</button>
  <button @click="next()">下一张</button>
</div>
</template>

<script>
  import slider from './components/Slider'
  export default {
    components: {
      slider
    },
    data(){
      return {
        slides: [{
          "title": "为什么说现阶段向淘宝店与微商征税并不公平？",
          "value": "http://laotie.baijia.baidu.com/article/815629",
          "image": "http://myweb-10017157.cossh.myqcloud.com/2017/0404/2fdda3cc7cd98d10048755ef283fb80e7aec9098.jpg",
          "type": 2,
          "weight": 1,
          "remark": "",
          "hash": "2fdda3cc7cd98d10048755ef283fb80e7aec9098"
        },
        {
          "title": "乌鲁木齐清明时节雪纷飞",
          "value": "http://news.china.com.cn/2017-04/04/content_40554966.htm",
          "image": "http://myweb-10017157.cossh.myqcloud.com/2017/0404/b2de9c82d158ccbfae4c5ee410d8bc3eb0354178.jpg",
          "type": 2,
          "weight": 2,
          "remark": "",
          "hash": "b2de9c82d158ccbfae4c5ee410d8bc3eb0354178"
        },
        {
          "title": "社会各界人士祭女飞行员余旭烈士",
          "value": "http://news.ifeng.com/a/20170404/50885615_0.shtml?_zbs_baidu_news#p=1",
          "image": "http://myweb-10017157.cossh.myqcloud.com/2017/0404/b3119313b07eca80a21a9b39982397dda04483d5.jpg",
          "type": 1,
          "weight": 3,
          "remark": "",
          "hash": "b3119313b07eca80a21a9b39982397dda04483d5"
        }]
      }
    },
    methods: {
      onSlideChangeStart: function (currentPage) {
        console.log('onSlideChangeStart', currentPage);
      },
      onSlideChangeEnd: function (currentPage) {
        console.log('onSlideChangeEnd', currentPage);
      },
      onSlideRevertStart: function (currentPage) {
        console.log('onSlideRevertStart', currentPage);
      },
      onSlideRevertEnd: function (currentPage) {
        console.log('onSlideRevertEnd', currentPage);
      },
      onSliderMove: function (offset) {
        console.log('onSliderMove', offset);
      },
      prependSlide: function (slideText) {
        this.slides.unshift({
          "title": "bajian prepend",
          "value": "#",
          "image": "http://i0.hdslb.com/bfs/archive/cf6153a50cb0f3eb27a5836d90be16d4bce8c6f7.jpg",
        });
      },
      appendSlide: function (slideText) {
        this.slides.push({
          "title": "bajian append",
          "value": "#",
          "image": "http://i0.hdslb.com/bfs/archive/cf6153a50cb0f3eb27a5836d90be16d4bce8c6f7.jpg",
        });
      },
      prev: function () {
        console.log('prev click');
        window.t=this;
        this.$refs.test_prev_next.prev();
      },
      next: function () {
        console.log('next click');
        window.t=this;
        this.$refs.test_prev_next.next();
      }
    }
  }
</script>

```

## Api
### Properties
| Name                 | Type      | Default      | Description                                                        |
|----------------------|-----------|--------------|------------------------------------------------------------------|
| mousewheel-control   | `Boolean` | `true`       | Set true to enable navigation through slides using mouse wheel. |
| pagination-visible   | `Boolean` | `false`      | Toggle (hide/true) pagination container visibility when click on Slider's container    |
| performace-mode      | `Boolean` | `false`      | Disable animation for better performance for bad android.      
| slides      | `Array` | `[]`      | the banner data just be used to observe by pagination when you add or remove a child slide  
| repeating      | `Boolean` | `false`      | Set true to enable repeating from last to first or first to last                 |
| auto      | `Number` | `0`      | Set to 0ms to disable silders auto change     |
| ==================== | ========= | ============ | =================== |

### Events
| Name                            | Parameters | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| slide-change-start | `pageNumber`     | Fire in the beginning of animation to other slide (next or previous).                                                                                        |
| slide-change-end   | `pageNumber`     | Will be fired after animation to other slide (next or previous).                                                                                             |
| slide-revert-start | `pageNumber`     | Fire in the beginning of animation to revert slide (no change).                                                                                              |
| slide-revert-end   | `pageNumber`     | Will be fired after animation to revert slide (no change).                                                                                                   |
| slider-move        | `offset`         | Callback function, will be executed when user touch and move finger over Swiper and move it. Receives swiper instance and 'touchmove' event as an arguments. |
| ================== | ================ | ============================ |

### Methods
| Name                            | Parameters | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| next() | no     | call it to slide to the next slider eg:this.$refs.test_prev_next.next();                                                                                        |
| prev()   | no     | call it to slide to the previous slider eg:this.$refs.test_prev_next.prev();                                                                                            |
| ================== | ================ | ============================ |

