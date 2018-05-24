Vue的图片查看组件

### 安装
```
npm i vue-simple-picture-preview -S
```

### 引入

test.vue
```
<template>

  <VuePicturePreview :pictureList="pictureList"></VuePicturePreview>

</template>

import VuePicturePreview from 'vue-simple-picture-preview';
export default {
    data() {
      return {
        pictureList: []
      }
    },
    components: {
      VuePicturePreview
    }
  }
```

### 数据格式

基础数据格式
```
pcitureList: [
          'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1527055313908&di=6d5e33060227a77b855732239f6ec791&imgtype=0&src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F038490758b8eb35a801219c779c8f19.jpg',
          'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1527055341963&di=d61fcca00e3d402170829098cb69bf9d&imgtype=0&src=http%3A%2F%2Fpic76.nipic.com%2Ffile%2F20150814%2F10825287_120646612000_2.jpg',
          'https://timgsa.baidu.com/timg?image&quality=80&size=b10000_10000&sec=1527045277&di=5f6b675ed2106e8d3404262f596178e2&src=http://pic39.nipic.com/20140313/2531170_174802041351_2.jpg'
        ]
```

对象集合

在该数据格式下我们首先发现链接都只有一部分，没有域名，并且是键值对的形式，所以我们需要配置参数
```
<PictureView
      :pictureList="pictureList"
      :props="defaultProps"
    ></PictureView>

 data() {
   return {
     pictureList: [
       {
         origine: '/timg?image&quality=80&size=b9999_10000&sec=1527055313908&di=6d5e33060227a77b855732239f6ec791&imgtype=0&src=http%3A%2F%2Fimg.zcool.cn%2Fcommunity%2F038490758b8eb35a801219c779c8f19.jpg'
       },{
         origine: '/timg?image&quality=80&size=b9999_10000&sec=1527055341963&di=d61fcca00e3d402170829098cb69bf9d&imgtype=0&src=http%3A%2F%2Fpic76.nipic.com%2Ffile%2F20150814%2F10825287_120646612000_2.jpg'
       },{
         origine: '/timg?image&quality=80&size=b10000_10000&sec=1527045277&di=5f6b675ed2106e8d3404262f596178e2&src=http://pic39.nipic.com/20140313/2531170_174802041351_2.jpg'
       }
     ],
     defaultProps: {
       key: 'origine',
       domain: 'https://timgsa.baidu.com'
     }
   }
  }
```


### 其他配置参数
```
isRotate  // 是否显示旋转，默认true
isMove // 是否显示前进后退，默认true
isScale // 是否显示放大缩小，默认true
isClikcImgClose  // 是否开启点击图片关闭弹出层，默认false
isMenu // 是否显示按钮栏，默认true
doubleRestore // 双击恢复图片初始状态, 默认true
isMousewheelScale // 鼠标滚轮缩放，默认true
```

### 接口

move // 前进后退时候的派发事件，返回字段

```
direction // 1为前进，-1位后退
src // 当前显示的图片地址
index // 当前图片索引值
isFirst // 是否为第一张
isLast // 是否为最后一张
```

```
 <PictureView
      :pictureList="pictureList"
      :isMenu="true"
      :isRotate="false"
      :isMove="true"
      :isScale="false"
      :isClikcImgClose="true"
      :isMousewheelScale="true"
      :doubleRestore="false"
      @move="handleMove"
    ></PictureView>
```
