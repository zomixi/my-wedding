<template>
  <div class="invitation invitation-bounce" @click="close">
    <div class="invitation-container" :class="{ 'invitation-down': isOpening }">
      <div class="invitation-cover">
        <div class="cover-content" :class="{ opening: isOpening }">
          <div class="content-inside">
            <img class="content-inside-photo" src="../assets/photo.jpg" />
            <p class="content-inside-text">我们结婚啦！</p>
            <p class="content-inside-text"><b>Zhong</b> & <b>Xiao</b></p>
            <p class="content-inside-text">时间：<b>2024-04-27</b></p>
            <p class="content-inside-text">地点：<b>世纪大酒店</b></p>
          </div>
        </div>
        <div class="cover-inside-left" :class="{ opening: isOpening }"></div>
        <div class="cover-inside-right" :class="{ opening: isOpening }"></div>
        <img class="cover-inside-seal" src="../assets/seal.png" @click.stop="open"
          :class="{ 'invitation-flight': isOpening }" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpening: false,
    };
  },
  methods: {
    open() {
      this.isOpening = true;
    },
    close() {
      this.isOpening = false;
    },
  },
};
</script>

<style lang="less">
.invitation {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  padding: 30px 20px;
  padding-top: 60px;
  z-index: 4;
  transform: scale(0.05);
  opacity: 0;
  transition: transform 0.8s cubic-bezier(0.26, 1.84, 0.39, 0.61),
    opacity 0.5s linear;
  background-size: 100%;
  overflow: hidden;
}

.invitation-container {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s cubic-bezier(0.4, 0, 1, 1);
}

.invitation-down {
  transform: translateY(20px);
}

.invitation-cover {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #d65047;
  border-radius: 10px;
  perspective: 500px;
  box-shadow: 0 0 20px 2px rgba(0, 0, 0, 0.15);
}

.cover-content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  padding: 10px 20px;
  transition: transform 0.6s cubic-bezier(0.4, 0, 1, 1);
}

.cover-content.opening {
  transform: translateY(-60px);
}

.content-inside {
  height: 100%;
  padding: 20px;
  color: #a9895d;
  background-color: #fff1de;
  text-align: center;
  overflow: auto;
}

.content-inside-photo {
  width: 100%;
  margin-bottom: 10px;
  padding: 5px;
  border: 1px solid #f7debb;
}

.content-inside-text {
  margin-bottom: 8px;
}

.cover-inside-left {
  position: absolute;
  left: 0;
  top: 0;
  width: 70%;
  height: 100%;
  border-radius: 10px;
  background-color: #d65047;
  box-shadow: 5px 0 10px rgba(0, 0, 0, 0.2);
  z-index: 6;
  transition: transform 0.5s;
  transform-origin: 0 50%;
}

.cover-inside-left.opening {
  transform: rotate3d(0, 1, 0, -140deg);
}

.cover-inside-right {
  position: absolute;
  right: 0;
  top: 0;
  width: 40%;
  height: 100%;
  border-radius: 10px;
  background-color: #d65047;
  box-shadow: -5px 0 10px rgba(0, 0, 0, 0.2);
  z-index: 5;
  transition: transform 0.5s;
  transform-origin: 100% 50%;
}

.cover-inside-right.opening {
  transform: rotate3d(0, 1, 0, 140deg);
}

.cover-inside-seal {
  position: absolute;
  left: 70%;
  bottom: 100px;
  width: 80px;
  height: 80px;
  margin-left: -40px;
  z-index: 7;
  transform-origin: 50% 50%;
  transition: all 0.8s cubic-bezier(0.4, 0, 1, 1);
}

.invitation-flight {
  opacity: 0;
}

.invitation-bounce {
  opacity: 1;
  transform: scale(1);
}
</style>
