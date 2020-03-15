# vue-shop

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).



<!-- git指令 -->
<!-- git checkout -b '分支名' -->

<!-- 查看分支 -->
<!-- git branch -->


<!--登录页面流程 -->
<!-- 1:静态页面书写
2:表单认证
3:使用axios请求并设置基准地址
4:保存用户成功的token标识符
5:使用路由守卫判断用户是否有登录 没登录不可跳转权限页面 
router.beforeEach((to, from, next) => {
    to:要去的路由
    form:来自哪个路由
    next:放行
  if (to.path === '/login') return next()
  const usertoken = window.localStorage.getItem('token')
  if (!usertoken) return to.next('/login')
  next()
})

-->