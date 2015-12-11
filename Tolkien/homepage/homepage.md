* [./](./content/README.md)

###首页专栏

* 说明:返回APP首页最上方运营位展示的数据

* 请求方法：GET

* 请求URL：/columns

* 返回说明：返回column的数组

* 返回示例：

```javascript
{
    [
        {
          "title": "买棉衣吧",
          "images": [
            {
              "url": "http://images.taozilvxing.com/a79d02ad1c9d8c3c75eadc92bb2acfd1"
            },
            {
              "url": "http://images.taozilvxing.com/cde4d5cc24b29aee2a93db5ebc28fbe1"
            }
          ],
          "link": "http://www.baidu.com"
        },
        {
          "title": "买内衣吧",
          "images": [
            {
              "url": "http://images.taozilvxing.com/a79d02ad1c9d8c3c75eadc92bb2acfd1"
            }
          ],
          "link": "http://www.baidu.com"
        }
    ]
}
```

* 字段说明
    * title: column的标题
    * link : 点击column图片后，app跳转的连接
    * images : column的图像的数组，显示第一个，其他的备用
    * 注意：接口中所有涉及到的图像，都采用这种images数组的形式给出


###今日特卖

* 说明:这个接口的文档没写完...

* 请求方法：GET

* 请求URL：/commodities?category=内衣

* 返回说明：返回今日特卖的内衣

* 返回示例：

```javascript
{
    [
        {
          "commodityId": 1000819,
          "images": [
            {
              "url": "http://images.taozilvxing.com/a79d02ad1c9d8c3c75eadc92bb2acfd1"
            }
          ],
          "title": "巴拉巴拉全面内衣"
        },
        {
          "commodityId": 1000819,
          "images": [
            {
              "url": "http://images.taozilvxing.com/a79d02ad1c9d8c3c75eadc92bb2acfd1"
            }
          ],
          "title": "GAP全面内衣"
        }
    ]
}
```

* 字段说明
    * title: 商品名称
    * images : 商品图片，默认显示第一个