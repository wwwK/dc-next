# DC-SDK

<p>
<img src="https://img.shields.io/github/workflow/status/dvgis/dc-sdk/publish"/>
<img src="https://img.shields.io/badge/license-Apache%202-blue"/>
<img src="https://img.shields.io/npm/v/@dvgis/dc-sdk?color=orange&logo=npm" />
<img src="https://img.shields.io/npm/dm/@dvgis/dc-sdk?logo=npm"/>
</p>

[**ð¨ð³ ä¸­æ**](./README_zh.md) | [**ð¬ð§English**](./README.md)

> DC-SDK æ¯åºäº Cesium è¿è¡äºæ¬¡å¼åç2ã3Dä¸ä½ WebGis åºç¨æ¡æ¶,è¯¥æ¡æ¶ä¼åäº Cesium çä½¿ç¨æ¹å¼åå¢æ·»äºä¸äºé¢å¤åè½ï¼æ¨å¨ä¸ºå¼åèå¿«éæå»º WebGis åºç¨ã

##ä¸»é¡µ

> http://dc.dvgis.cn

```warning
Tipsï¼æ¬æ¡æ¶æ¯ JS+GIS çæ¡æ¶åãå¼åèéè¦æä¸å®çåç«¯ææ¯å GIS ç¸å³ææ¯
```

## å®è£

`CDN`

```html
<!--åºç¡å-->
<script src="libs/dc-sdk/dc.base.min.js"></script>
<!--æ ¸å¿å-->
<script src="libs/dc-sdk/dc.core.min.js"></script>
<!--ä¸»è¦æ ·å¼-->
<link href="libs/dc-sdk/dc.core.min.css" rel="stylesheet" type="text/css" />
```
 
`NPM / YARN`

```shell
yarn add @dvgis/dc-sdk
npm install @dvgis/dc-sdk
```

```js
import DC from 'dvgis/dc-sdk/dist/dc.base.min' //åºç¡å
import DcCore from  'dvgis/dc-sdk/dist/dc.core.min' //æ ¸å¿å
import 'dvgis/dc-sdk/dist/dc.core.min.css' // ä¸»è¦æ ·å¼
```

## éç½®

`Webpack`

```js
 // webpack.config.js

const path = require('path')
const CopywebpackPlugin = require('copy-webpack-plugin')
const dvgisDist = './node_modules/@dvgis'

module.exports = {
  // å¶ä»éç½®
  resolve: {
    alias: {
      dvgis: path.resolve(__dirname, dvgisDist)
    }
  },
  plugins:[
    new CopyWebpackPlugin([
      {  
        from: path.join(dvgisDist, 'dc-sdk/dist/resources'),
        to: 'libs/dc-sdk/resources' 
      }
    ])
  ]
}
```

`Vue2.x`

```js
// vue.config.js

const path = require('path')
const CopywebpackPlugin = require('copy-webpack-plugin')
const dvgisDist = './node_modules/@dvgis'

module.exports = {
  // å¶ä»éç½®
  chainWebpack: config => {
    config.resolve.alias.set('dvgis', path.resolve(__dirname, dvgisDist))
    config.plugin('copy').use(CopywebpackPlugin, [
      [
        {
          from: path.join(dvgisDist, 'dc-sdk/dist/resources'),
          to: 'libs/dc-sdk/resources'
        }
      ]
    ])
  }
}
```

`Vue3.x`

```js
// vue.config.js

const path = require('path')
const CopywebpackPlugin = require('copy-webpack-plugin')
const dvgisDist = './node_modules/@dvgis'

module.exports = {
  // å¶ä»éç½®
  chainWebpack: config => {
    config.resolve.alias.set('dvgis', path.resolve(__dirname, dvgisDist))
    config.plugin('copy').use(CopywebpackPlugin, [
      {
        patterns: [
          {
            from: path.join(dvgisDist, 'dc-sdk/dist/resources'),
            to: path.join(__dirname, 'dist', 'libs/dc-sdk/resources'),
          },
        ],
      }
    ])
  }
}
```

## å¼å§

```js
global.DC = DC
DC.use(DcCore) // Node æ¹å¼
DC.ready(() => {
  let viewer = new DC.Viewer(divId) // divId ä¸ºä¸ä¸ªdivèç¹çIdå±æ§å¼ï¼å¦æä¸ä¼ å¥ï¼ä¼æ æ³åå§å3Dåºæ¯
})
```

## ææ¡£

[DC Sdk  Api](https://resource.dvgis.cn/dc-api)

[Cesium Api](https://cesium.com/docs/cesiumjs-ref-doc/)

## ç¤ºä¾

|  ![picture](http://dc.dvgis.cn/examples/images/baselayer/baidu.png?v=1) | ![picture](http://dc.dvgis.cn/examples/images/baselayer/tdt.png?v=1) | ![picture](http://dc.dvgis.cn/examples/images/baselayer/arcgis.png?v=2) | ![picture](http://dc.dvgis.cn/examples/images/mini-scene/china.gif) |
|  :-----------------------------------------------------------: | :-----------------------------------------------------------: | :------------------------------------------------------------------: | :--------------------------------------------------------------: |
|  ![picture](http://dc.dvgis.cn/examples/images/mini-scene/dfmz.gif) | ![picture](http://dc.dvgis.cn/examples/images/mini-scene/factory.gif?v=1) | ![picture](http://dc.dvgis.cn/examples/images/layer/cluster_circle.gif) | ![picture](http://dc.dvgis.cn/examples/images/model/shp_custom_shader.gif) |
|  ![picture](http://dc.dvgis.cn/examples/images/overlay/polyline_image_trail.gif) | ![picture](http://dc.dvgis.cn/examples/images/overlay/wall_trail.gif?v=1) | ![picture](http://dc.dvgis.cn/examples/images/overlay/water.gif?v=2)  |  ![picture](http://dc.dvgis.cn/examples/images/overlay/plot-overlay.png)   |

[æ´å¤>>](http://dc.dvgis.cn/#/examples)

## çæ

|  æ¨¡ååç§° | ç¶æ | æè¿° | 
|  :------ | :------: | :------ | 
| [dc-plugins](https://github.com/dvgis/dc-plugins) | <img src="https://img.shields.io/npm/v/@dvgis/dc-plugins?logo=npm" /> | DCæä»¶æ¨¡åï¼åæ¬åºæ¯å¨ç»ãæ¼«æ¸¸ä»¥åä¸äºé¢å¤çæè´¨ | 
| [dc-overlay](https://github.com/dvgis/dc-overlay) | <img src="https://img.shields.io/npm/v/@dvgis/dc-overlay?logo=npm" /> | DCè¦ç´ æ¨¡åï¼åæ¬çä½ãæ±ä½ãåæ ãæ°´é¢ç­ | 
| [dc-plot](https://github.com/dvgis/dc-plot) | <img src="https://img.shields.io/npm/v/@dvgis/dc-plot?logo=npm" /> | DCæ ç»æ¨¡åï¼ç¨äºè¦ç´ çæ ç»åç¼è¾ | 
| [dc-chart](https://github.com/dvgis/dc-chart) | <img src="https://img.shields.io/npm/v/@dvgis/dc-chart?logo=npm" /> | DCå¾è¡¨æ¨¡åï¼ç¨äºå¨ä¸ç»´åºæ¯ä¸­æ·»å Echartsåè½ | 
| [dc-mapv](https://github.com/dvgis/dc-mapv) | <img src="https://img.shields.io/npm/v/@dvgis/dc-mapv?logo=npm" /> | DCå¤§æ°æ®æ¨¡åï¼ç¨äºå¨ä¸ç»´åºæ¯ä¸­æ·»å Mapvåè½ | 
| [dc-ui](https://github.com/dvgis/dc-ui) | <img src="https://img.shields.io/npm/v/@dvgis/dc-ui?logo=npm" /> | DCåºäºVue2.xç»ä»¶å¼åæ¡æ¶ï¼å°DCåè½Vueæ¨¡åå | 
|  dc-analysis | <img src="https://img.shields.io/npm/v/@dvgis/dc-analysis?logo=npm" /> |  DCåææ¨¡åï¼åæ¬è§é¢èåï¼ä½ç½®ç¼è¾ãæµéç­ |
|  dc-ui-next | <img src="https://img.shields.io/npm/v/@dvgis/dc-ui-next?logo=npm" /> | DCåºäºVue3.xç»ä»¶å¼åæ¡æ¶ï¼å°DCåè½Vueæ¨¡åå |

## QQ ç¾¤

<p>
<img src="http://dc.dvgis.cn/examples/images/base/q1.png?v=2" style="width:60px;height:60px" title="æ°å­è§è§"/>
<img src="http://dc.dvgis.cn/examples/images/base/q2.png?v=6" style="width:60px;height:60px" title="Cesiumå¼å¿ååº"/>
</p>

## æ¯æ

> å¦ædc-sdkè½å¤ç»æ¨å¸¦æ¥æçï¼è¯·æ¯æä¸ä¸å~
<p>
<img src="http://dc.dvgis.cn/examples/images/base/sponsor.jpg?v=2" style="width:60px;height:60px" title="æ°å­è§è§"/>
</p>

## çæå£°æ

```warning
1.æ¡æ¶ä½ä¸ºä¸ä¸ªåºç¡å¹³å°ï¼ä»£ç å¼æºï¼ä»»ä½ä¸ªäººåæºæå¯ä»¥ä¿®æ¹ãéæï¼æ éç»è¿ææ¹ææã
2.ä»»ä½ä¸ªäººåæºæä¿®æ¹æ¡æ¶åºç°çé®é¢ï¼ææ¹æ éè´è´£ã
3.åæä¼æ·»å ä¸äºè¡ä¸æ§çæä»¶åå·¥å·ï¼ä»£ç ä¼ééå¼æºã
4.å¯¹äºææ¹åå¸çç¨åºåï¼ä»»ä½ä¸ªäººåæºæå¨éµå®ä¸åæ¡ä»¶çåæä¸å¯ä»¥æ°¸ä¹åè´¹ä½¿ç¨:
   1)ç¨åºåå®æ´å¼ç¨ï¼
   2)ä¿çæ­¤çæä¿¡æ¯å¨æ§å¶å°è¾åº
ææ¹ä¿çå¯¹æ­¤çæä¿¡æ¯çæç»è§£éæã
```

## è°¢è°¢
