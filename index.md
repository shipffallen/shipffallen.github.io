Vue-cli 3.0 初体验 ！ 
```
// 前端社区你不要这么拼好不好？
回到正题：Vue-cli 是Vue 官方提供的脚手架工具，他的github 地址是：vue-cli github
如果你要体验最新的 3.0 aplha 版本，可以通过
npm install -g vue@cli
可以安装最新的vue-cli，然后你就可以使用来初始化你的项目
vue create <your project> 
注意：现在已经不是选择模版了，而是presets （预设）
首先是问你是否使用默认的preset 还是手动配置功能


如果你选择手动选择，则是一个多选的界面，可以使用 空格键选中或是取消， a键选中所有，i键反选
```
```
选好了以后，还会询问一系列的问题，比如使用哪一个CSS预处理器，是否把以上的所有的功能选择保存为一个下次可以用的 preset ？
是否选择淘宝镜像安装？十分贴心啊
等安装好了以后，就可以直接进入项目，使用
npm run serve 
来启动项目，注意：这里不在是之前的npm run dev 了...
点开package.json就会发现scripts 中的内容是：
"scripts": {
    "serve": "vue-cli-service serve --open",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
  }
vue-cli-service ?!! 这个是什么鬼？？这个肯定是vue 学习 react-scripts 搞了一个vue-cli-service 啊~
上面三个命令分别是启动开发服务，打包，和格式化你得代码
项目目录一下清晰很多：


等等~~ 之前的config目录哪里去了？build 的目录哪里去了？webpack 配置没有啊~~ 看来还是无配置的流行啊~~
那么我们怎么配置呢？要请出我们的vue.config.js 了，不用像其他的 create-react-app 或是 angular-cli生成的的项目一样去eject 配置，通过在项目下设置vue.config.js 我们就可以配置开发中所需要的多数部分。
官方配置文档
module.exports = {
  // Project deployment base
  // By default we assume your app will be deployed at the root of a domain,
  // e.g. https://www.my-app.com/
  // If your app is deployed at a sub-path, you will need to specify that
  // sub-path here. For example, if your app is deployed at
  // https://www.foobar.com/my-app/
  // then change this to '/my-app/'
  baseUrl: '/',

  // where to output built files
  // 打包后的输出目录
  outputDir: 'dist',

  // whether to use eslint-loader for lint on save.
  // 保存时是不是用eslint-loader 来lint 代码
  lintOnSave: false,

  // use the full build with in-browser compiler?
  // https://vuejs.org/v2/guide/installation.html#Runtime-Compiler-vs-Runtime-only
  // 使用runtime-only 还是 in-browser compiller
  compiler: false,

  // tweak internal webpack configuration.
  // see https://github.com/vuejs/vue-cli/blob/dev/docs/webpack.md
  // webpack 配置~
  chainWebpack: () => {},
  configureWebpack: () => {},

  // vue-loader options
  // https://vue-loader.vuejs.org/en/options.html
  // vue-loader 配置
  vueLoader: {},

  // generate sourceMap for production build?
  // 生产环境的sourceMap 要不要？
  productionSourceMap: true,

  // CSS related options
  css: {
    // extract CSS in components into a single CSS file (only in production)
    extract: true,

    // enable CSS source maps?
    sourceMap: false,

    // pass custom options to pre-processor loaders. e.g. to pass options to
    // sass-loader, use { sass: { ... } }
    loaderOptions: {},

    // Enable CSS modules for all css / pre-processor files.
    // This option does not affect *.vue files.
    // 用不用 css Modules 啊？
    modules: false
  },

  // use thread-loader for babel & TS in production build
  // enabled by default if the machine has more than 1 cores
  // 使用多线程否？
  parallel: require('os').cpus().length > 1,

  // split vendors using autoDLLPlugin?
  // can also be an explicit Array of dependencies to include in the DLL chunk.
  // See https://github.com/vuejs/vue-cli/blob/dev/docs/cli-service.md#dll-mode
  // 用不用 autoDLLPlugin，厉害了
  dll: false,

  // options for the PWA plugin.
  // see https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-pwa
  // pwa 相关
  pwa: {},

  // configure webpack-dev-server behavior
  // Webpack dev server
  devServer: {
    open: process.platform === 'darwin',
    host: '0.0.0.0',
    port: 8080,
    https: false,
    hotOnly: false,
    // See https://github.com/vuejs/vue-cli/blob/dev/docs/cli-service.md#configuring-proxy
    proxy: null, // string | Object
    before: app => {}
  },

  // options for 3rd party plugins
  pluginOptions: {
    // ...
  }
}
```
