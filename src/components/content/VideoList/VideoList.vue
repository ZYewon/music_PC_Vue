<template>
  <div class="video-list">
    <div class="video-cover-img" @click="playVideoClick">
      <!-- 视频播放数量 -->
      <p class="play-count-bg">
        <span
          ><i class="iconfont icon-bofangqi-bofang"></i
          >{{ PlayCount | formatPlayCount }}</span
        >
      </p>
      <!-- 视频封面 -->
      <img v-lazy="imageSrc" :key="imageSrc" alt="" />
      <!-- 视频视长 -->
      <span class="video-dt">{{ dt | formatTimer }}</span>
    </div>
    <div class="video-info">
      <!-- 视频名字 -->
      <h5 @click="playVideoClick">{{ videoName }}</h5>
      <!-- 视频作者 -->
      <p v-if="nicName && !mv">
        <i>by</i> <span>{{ nicName }}</span>
      </p>
      <p v-if="mv && creator.length">
        <em class="mv-icon"></em>
        <i class="mv-artist-name" v-for="(item, index) in creator" :key="index">
          {{ item.userName }}
          <em>{{ index === creator.length - 1 ? "" : "/" }}</em>
        </i>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoList",
  props: {
    PlayCount: {
      type: Number,
      default: 0,
    },
    imageSrc: {
      type: String,
      default: "",
    },
    dt: {
      type: Number,
      default: 0,
    },
    videoName: {
      type: String,
      default: "",
    },
    nicName: {
      type: String,
      default: "",
    },
    mv: {
      type: Boolean,
      default: false,
    },
    creator: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  methods: {
    playVideoClick() {
      this.$emit("playClick");
    },
  },
};
</script>
<style lang="less" scoped>
.video-list {
  width: 300px;
  margin: 15px 0;
  .video-cover-img {
    position: relative;
    width: 100%;
    height: 180px;
    cursor: pointer;
    .play-count-bg {
      position: absolute;
      top: 0;
      left: 0;
      height: 30px;
      width: 100%;
      border-radius: 10px;
      background-image: linear-gradient(
        rgba(0, 0, 0, 0.2),
        rgba(0, 0, 0, 0.1),
        rgba(0, 0, 0, 0)
      );
      z-index: 1;
      text-align: right;
      line-height: 25px;
      span {
        font-size: 14px;
        margin-right: 10px;
        color: #fff;
      }
    }
    img {
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      border-radius: 10px;
    }
    .video-dt {
      position: absolute;
      right: 10px;
      bottom: 10px;
      font-size: 12px;
      color: #fff;
    }
  }
  .video-info {
    margin-top: 10px;
    h5 {
      font-size: 14px;
      color: #373737;
      width: 100%;
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
      cursor: pointer;
    }
    p {
      margin-top: 10px;
      display: flex;
      i {
        font-size: 12px;
        color: #cfcfcf;
        cursor: default;
      }
      span {
        flex: 1;
        font-size: 12px;
        margin-left: 5px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        cursor: pointer;
      }
    }
    .mv-icon {
      width: 20px;
      height: 12px;
      margin-right: 5px;
      display: inline-block;
      background: url("~@/assets/img/mvIcon.png") no-repeat;
      background-size: 100%;
    }
    .mv-artist-name:hover {
      color: #373737;
    }
  }
}
</style>