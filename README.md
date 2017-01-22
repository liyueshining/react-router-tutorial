React Router Tutorial
=====================

Quick lessons for getting up-to-speed with React Router.

See [Lesson 1 - Setting Up](/lessons/01-setting-up/) to get started.

Each lesson is a fully runnable app with all code from the previous lesson, so you can `cd lessons/<lesson-folder>`, npm install,
and then run the appropriate NPM scripts for each lesson from within the lesson folder.

Missing stuff that will come eventually, hopefully ... maybe.

1. an app that isn't completely pointless

    - egghead.io videos
    - code splitting
    - location state
    - data integration



2. react路由history三种模式

React Router 是建立在 history 之上的。 简而言之，一个 history 知道如何去监听浏览器地址栏的变化， 并解析这个 URL 转化为 location 对象， 然后 router 使用它匹配到路由，最后正确地渲染对应的组件。
常用的 history 有三种形式， 也可以使用 React Router 实现自定义的 history。

   - hashHistory
        
     react-router默认 history ，它用到的是 URL 中的 hash（#）部分去创建形如 http://aa.bb.com/#/help 的路由。
     支持 ie8＋，因为是 hash 值，不推荐使用。
   - browserHistory
    
    browserHistory 是由 React Router 创建浏览器应用推荐的 history。它使用 History API 在浏览器中被创建用于处理 URL，新建一个像这样真实的           URL http://aa.bb.com/help。
   - memoryHistory
    不会在地址栏被操作或读取。
    
    
使用hashHistory，因为用的#hash 方式，真正的url没变。变的只是hash值，所以下次直接访问http://aa.bb.com/#/help 就能直接访问，但是这种模式不利于SEO，不推荐使用。

使用browserHistory，因为是使用 History API处理url的，真实的url已经改变，当我们重新刷新浏览器，内部已经重置，我们下次再访问地址http://aa.bb.com/help 的时候，之前的history已经更新，相当于直接到服务器去请求这个url，当然我们用的是前端路由，服务器肯定不知道这个是啥咯，所以返回404页面。要解决该问题 就需要在服务端设置 接受到请求的时候 都指向 index.html文件，详见 lession 12


3. 使用中发现的问题

    使用的浏览器 chrome（Firefox没有这样的问题），react-router， IndexRoute 中指向的组件是一个form， form内有有一个按钮，没有设置type，按钮的点击事件里 定义了一个browserHistory.push('/oki/install')， 这样在跳转到 /oki/install 路径时 结尾会自动带上一个'?'号， 为避免这种情况 可以把按钮的点击事件定义为 form的提交事件，或者 不用form。
