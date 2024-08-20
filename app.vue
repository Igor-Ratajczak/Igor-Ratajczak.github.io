<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style lang="less">
  @import url('~/assets/style.less');
  .page-leave-active {
    transition: all 0.8s ease;
  }
  .page-enter-active {
    transition: all 0.8s ease;
    transform: translateX(150%) scale(0.3);
  }
  .page-after-enter {
    transform: translateX(150%) scale(0.3);
  }
  .page-enter-to {
    animation: enter 0.8s forwards;
  }
  //   .page-enter-to {
  //     transform: translateX(0) scale(1);
  //   }
  @keyframes enter {
    0% {
      transform: translate(150%) scale(0.3);
    }
    50% {
      transform: translate(0) scale(0.3);
    }
    100% {
      transform: translate(0%) scale(1);
    }
  }
  .page-leave-to {
    // opacity: 0;
    animation: from 0.8s forwards;
  }
  @keyframes from {
    0% {
      transform: translate(0%) scale(1);
    }
    50% {
      transform: translate(0) scale(0.3);
    }
    100% {
      transform: translate(-150%) scale(0.3);
    }
  }
  //   .page-enter-from {
  //     transform: rotateY(180deg);
  //   }
  //   .page-leave-to {
  //     transform: rotateY(180deg);
  //   }
</style>
