<template>
  <div id="home">
    <Swiper />
    <Title describe="推荐歌单" link="/playlist" />
    <Songsheet />
    <Title describe="独家放送" link="/sole" />
    <Release />
    <Title describe="最新音乐" link="/new-song" />
    <NewSong />
    <Title describe="推荐MV" link="/mv" />
    <ContainerMv />
  </div>
</template>

<script>
import Swiper from "@/components/content/Swiper/Swiper";
import Title from "@/components/common/Title/Title";
import Songsheet from "@/components/common/Songsheet/Songsheet";
export default {
  name: "Home",
  components: {
    Swiper,
    Title,
    Songsheet,
    Release: () => import("@/components/content/Release/Release"),
    NewSong: () => import("@/components/content/NewSong/NewSong"),
    ContainerMv: () => import("@/components/content/ContainerMv"),
  },
  mounted() {},
};
</script>

<style lang="less" scoped>
#home {
  flex: 1;
  height: 100%;
  overflow-y: auto;
  padding: 20px 40px;
}
</style>
