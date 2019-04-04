<template>
  <div class="alert">
    <div class="alert-main" v-for="item in notices" :key="item.name">
      <div
        class="alert-content"
        :class="{
                  success: item.type == 'success',
                  warn: item.type == 'warn',
                  fail: item.type == 'fail'
              }"
      >
      <img :src="item.icon">
      <span>{{ item.content }}</span>
      </div>
    </div>
  </div>
</template>
<script>
  let seed = 0;
  function getUuid() {
    return 'alert_' + (seed++);
  }

  export default {
    data() {
      return {
        notices: []
      }
    },
    mounted() {
      console.log(this.notices)
    },
    methods: {
      add(notice) {
        const name = getUuid();
        let _notice = Object.assign({
          name: name
        }, notice);
        this.notices.push(_notice);
        // 定时移除，单位：秒
        const duration = notice.duration;
        setTimeout(() => {
          this.remove(name);
        }, duration * 1000);
      },
      remove(name) {
        const notices = this.notices;
        for (let i = 0; i < notices.length; i++) {
          if (notices[i].name === name) {
            this.notices.splice(i, 1);
            break;
          }
        }
      }
    }
  }
</script>
<style>
  .alert {
    position: fixed;
    width: 100%;
    top: 16px;
    left: 0;
    text-align: center;
    pointer-events: none;
    border-radius: 10px;
  }

  .alert-content {
    display: inline-block;
    padding: 5px;
    width: 150px;
    border-radius: 8px;
    margin-bottom: 8px;
    height: 30px;
    line-height: 30px;
  }

  .alert .success {
    color: white;
    background: #43d786;
    box-shadow: 0 1px 6px #43d786;
  }

  .alert .warn {
    color: white;
    background: #f6714c;
    box-shadow: 0 1px 6px #f6714c;
  }

  .alert .fail {
    color: white;
    background: #eb5e5b;
    box-shadow: 0 1px 6px #eb5e5b;
  }
  .alert img{
    width: 15%;
    margin-right: 5px;
    vertical-align: middle;
  }
</style>