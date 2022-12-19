### Webpack对React的代码分割方案
---

*网上关于如何对React代码分割的文档有很多，但是系统完整的文章比较少，故本文是将现有方案完整列出，并做一定的分析讲解。*

##### 按照路由拆分

##### 缓存拆分node_modules公共代码库
   
##### 缓存拆分业务公共组件
   
##### 对页面单独分析
使用*webpack-bundle-analyzer*插件对页面单独分析

1. 拆分第三方库
2. 动态引入组件
  ```js
  useEffect(() => {
    import('./Plant').then((Plant) => {
      setPlant({ Comp: Plant.default });
    });
  }, []);
  ```

[1] React代码分割：https://zh-hans.reactjs.org/docs/code-splitting.html#reactlazy