# vue-alert
### 引入
把内容放在一个文件夹里，然后在<code>main.js</code>中引入
```javascript
import Vue from 'vue'
import App from './App.vue'
import Alert from './alert/alert'

Vue.config.productionTip = false;
Vue.prototype.$Alert = Alert;

new Vue({
  render: h => h(App),
}).$mount('#app')

```
### 调用
```javascript
this.$Alert.info({
      content: 'success',
      duration: 3,
      type: 'success',
      icon: 'http://129.204.88.180/wp-content/uploads/2019/03/success.png'
    });
    this.$Alert.info({
      content: 'warn',
      duration: 3,
      type: 'warn',
      icon: 'http://129.204.88.180/wp-content/uploads/2019/03/warn.png'
    });
    this.$Alert.info({
      content: 'fail',
      duration: 3,
      type: 'fail',
      icon: 'http://129.204.88.180/wp-content/uploads/2019/03/fail.png'
    });
```
### 效果

![](http://129.204.88.180/wp-content/uploads/2019/03/localhost_8080_-3-1.png)
