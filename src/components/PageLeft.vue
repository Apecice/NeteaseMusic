<template>
  <div class="page-left-nav">
    <div class="left-nav-bg"></div>
    <div class="avatar nav-line">
      <img class="avatar-img iconfont" @click="goToUser" v-if="user.avatarUrl" :src="user.avatarUrl" />
      <img class="avatar-img iconfont" @click="goToUser" src="../assets/img/u-no-avatar.png" v-if="!user.avatarUrl">
      <div class="icon-text" @click="goToUser">{{user.userId ? user.nickname : '来登录呀'}}</div>
    </div>
    <div class="nav-line">
      <a href="#/search">
        <i class="iconfont icon-search"></i>
        <div class="icon-text">寻觅</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/playlist">
        <i class="iconfont icon-playlist"></i>
        <div class="icon-text">歌单</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/recommend">
        <i class="iconfont icon-recommend"></i>
        <div class="icon-text">推荐</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/top">
        <i class="iconfont icon-top"></i>
        <div class="icon-text">榜单</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/download">
        <el-badge :value="downloadInfo.count" :hidden="downloadInfo.count === 0" class="item">
          <i class="iconfont icon-down"></i>
        </el-badge>
        <div class="icon-text">下载</div>
      </a>
    </div>
    <div class="nav-line nav-mode-simple">
      <a href="#/simple">
        <i class="iconfont icon-windmill"></i>
        <div class="icon-text">极简</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/setting">
        <i class="iconfont icon-setting"></i>
        <div class="icon-text">设置</div>
      </a>
    </div>
    <div class="nav-line">
      <a href="#/about">
        <i class="iconfont icon-version"></i>
        <div class="icon-text">关于</div>
      </a>
    </div>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex';
  export default {
    name: "PageLeft",
    computed: {
      ...mapGetters({
        user: 'getUser',
        downloadInfo: 'getDownloadInfo',
        mode: 'getMode',
      })
    },
    created() {

    },
    methods: {
      goToUser() {
        if (this.mode === 'simple') {
          return window.location = '#/';
        }
        window.location = '#/user';
      }
    }
  }
</script>

<style lang="scss">
  .mode-simple {
    .page-left-nav {
      height: 100px !important;
      width: 100px !important;
      border-radius: 50%;
      padding: 0;
      top: -40px;
      left: -40px;

      .avatar {
        margin-top: 0;
        width: 100px !important;
        height: 100px !important;

        .avatar-img {
          width: 100px !important;
          height: 100px !important;
        }
      }

      &:hover {
        transform: scale(1.5);
        top: -20px;
        left: -20px;
      }
    }
  }

  .mode-mobile {
    .page-left-nav {
      width: 100vw !important;
      height: 15vw !important;
      white-space: nowrap;
      overflow-x: auto;
      background: #fff5;
      position: fixed;
      z-index: 10;

      .left-nav-bg {
        display: none;
      }

      .avatar {
        margin: 2.5vw !important;
        width: 10vw !important;
        height: 10vw;
        .iconfont {
          display: inline-block !important;
        }
        .icon-text {
          display: none;
        }
      }

      .nav-mode-simple {
        display: none !important;
      }

      .nav-line {
        display: inline-block;
        width: 15vw;
        vertical-align: top;

        .iconfont {
          display: none;
        }

        .icon-text {
          width: 15vw;
          line-height: 15vw;
          padding-left: 0 !important;
          text-align: center;
          font-size: 3.4vw;
        }
      }
    }
  }
  .page-left-nav {
    position: absolute;
    left: 0;
    top: 0;
    width: 40px;
    padding: 0 10px;
    transition: 0.3s;
    overflow: hidden;
    color: #fff;
    height: 100%;
    font-size: 18px;
    font-weight: bold;
    border-radius: 0;
    opacity: 0.4;
    z-index: 100;

    .left-nav-bg {
      background: -webkit-linear-gradient(top, #fff8, #fff6, #fff0, #fff0);
      height: 200%;
      top: -50%;
      position: absolute;
      right: 0;
      width: 400px;
      transition: 0.3s;
    }

    &:hover {
      width: 270px;
      opacity: 1;

      .left-nav-bg {
        background: -webkit-linear-gradient(top, #ccc9, #ccc9, #ccc5, #ccc0, #ccc0, #ccc0);
        border-radius: 0 100% 200% 0;
      }

      .iconfont {
        opacity: 1;
      }
      .avatar {
        .avatar-img {
          width: 50px;
          height: 50px;
        }
      }
    }

    .avatar {
      margin-top: 30px;
      opacity: 0.8;

      .avatar-img {
        width: 40px;
        height: 40px;
        border-radius: 50%;
      }
    }
    .nav-line {
      width: 500px;
      line-height: 40px;
      height: 40px;
      margin-bottom: 20px;
      cursor: pointer;

      a {
        color: #fff !important;
      }

      &:hover {
        .iconfont {
          font-size: 36px;
          &.img {
            width: 50px;
            height: 50px;
          }
        }
        .icon-text {
          font-size: 22px;
        }
      }

      .iconfont {
        display: inline-block;
        vertical-align: top;
        font-size: 30px;
        font-weight: 100;
        opacity: 0.8;
        transition: 0.3s;
        width: 40px;
        text-align: center;
      }
      .icon-text {
        display: inline-block;
        vertical-align: top;
        opacity: 0.8;
        transition: 0.3s;
        padding-left: 20px;
        width: 300px;
      }
    }
  }
</style>