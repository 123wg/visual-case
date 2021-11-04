## 框架问题
- 完善stylelint 校验
- eslint校验完善 --采用最严格的代码规范校验
- vuex分包管理 命名空间
- 增加代码提交规范校验 0
- 引入element-plus 0

## 编辑器
- 禁用vulture 使用 volar
- 括号配对着色(Bracket Pair Colorizer) 插件
- 卸载 Vue VSCode Snippets 使用 Vue3 Snippets
```
    解决别名报错问题 
    https://www.jianshu.com/p/f3f03fa9ab42
    // "eslint-import-resolver-alias": "^1.1.2",
        // settings: {
    //     'import/extensions': ['.js', '.jsx', 'ts', 'tsx'],
    //     'import/resolver': {
    //         node: {
    //             extensions: ['.js', '.jsx', '.ts', '.tsx'], // 配置文件扩展名
    //         },
    //         // 配置alias
    //         alias: {
    //             map: [
    //                 ['@', './src'],
    //             ],
    //             extensions: ['.js', '.jsx', '.ts', '.tsx'],
    //         },
    //     },
    // },
```

## 编辑器技术调研
- blender 模型搭建测试
- 场景自适应 1
- 天空盒加载 1
- 绘制参考线 1
- 测试加载三维模型 1
- 鼠标事件监听(拖拽功能实现) 1
- 点击选中物体 ,物体选中效果 1
- 贴图的基础 1
- 光照效果 1
- 创建地面 1
- 墙体添加窗户 1
- 创建流动管道 1

v1.0.1
-----------设计------------
    - 拖拽物料区数据模型设计 0
    - 拖拽物料准备(地面，草坪，围墙，树),下载免费的gltf或者3dmax转
    - 事件管理器设计 0
    - 测试搭建园区外景 0
    - blender 搭建白墙模型测试 0
----------技术调研----------
    - 场景转动禁止事件
    - 鼠标拖拽移动物体
    - 加载dom节点

v1.0.2 TODO
-----------设计--------------
    - 层级管理器设计 0
    - 编辑展示各种状态模式设计 0
----------技术调研-----------
    - 顶点合并
    - 导入导出


