<template>
  <div>
    <header>
      <div class="logo">LOGO</div>
      <NuxtLink to="/"
        ><div class="item">
          <div class="icon"><homeVue /></div>
          <!-- <b>Strona główna</b> -->
        </div>
      </NuxtLink>
      <NuxtLink to="/projects"
        ><div class="item">
          <div class="icon"><homeVue /></div>
          <!-- <b>Moje projekty</b> -->
        </div>
      </NuxtLink>
      <NuxtLink to="/about"
        ><div class="item">
          <div class="icon"><homeVue /></div>
          <!-- <b>O mnie</b> -->
        </div>
      </NuxtLink>
    </header>
    <main>
      <slot />
    </main>
    <footer>
      <div class="copyright">
        Copyright © 2024 Igor Ratajczak © All rights reserved - Igor Ratajczak.
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
  import homeVue from './icons/home.vue'
</script>

<style lang="less">
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: var(--background-header);
    color: var(--color-header);
    padding: 10px;
    user-select: none;
    position: absolute;
    backdrop-filter: blur(5px);
    gap: 2em;
    z-index: 10000;

    @media screen and (max-height: 450px) {
      flex-direction: column;
      right: 0;
      width: 70px;
      height: 100vh;
      left: calc(100vw - 70px);
      border-radius: 25px 0 0 25px;
      top: 50%;
      transform: translate(0, -50%);
      border-radius: 20px 0 0 25px;
    }

    @media screen and (min-height: 451px) {
      flex-direction: row;
      bottom: 0;
      right: 50%;
      transform: translate(50%, 0);
      border-radius: 25px 25px 0 0;
    }
    @media screen and (max-width: 451px) {
      width: 100vw;
      gap: 10px;

      .logo.logo {
        flex-grow: 0;
      }
      .icon.icon {
        width: 30px;
        height: 30px;
        display: grid;
        place-content: center;
        padding: 0;

        svg {
          width: 20px;
          height: 20px;
        }
      }
    }

    > .logo {
      flex-grow: 1;
    }

    > a {
      color: white;
      text-decoration: none;

      .item {
        display: grid;
        justify-items: center;

        .icon {
          width: 50px;
          height: 50px;
          padding: 10px;
          border-radius: 25px;
          z-index: 10;
          position: relative;
          transition: transform 0.5s, box-shadow 0.5s 0.2s;
          background: radial-gradient(lightgreen, green);
          box-shadow: 0px 0px 50px 10px transparent;

          @media screen and (min-width: 1000px) and (min-height: 600px) {
            &:hover {
              transform: scale(1.3);
              box-shadow: 0px 0px 50px 10px green;
            }
            &:hover::before {
              animation: rotate 1s linear infinite forwards;
              animation-delay: 0ms;
            }
            @keyframes rotate {
              to {
                transform: rotate(360deg);
              }
            }
          }
        }
      }
    }
  }
  main {
    width: 100vw;
    height: 100%;
    text-align: center;

    @media screen and (min-width: 450px) {
      & {
        width: calc(100vw - 4em);
        left: 50%;
        position: relative;
        transform: translate(-50%);
      }
    }
    @media screen and (max-height: 450px) {
      width: calc(100vw - 70px);
      left: 0;
      transform: translate(0);
    }

    > div {
      background-color: rgba(0, 0, 0, 0.75);
      color: white;
      height: 100vh;

      > h1 {
        padding: 5px;
      }
    }
  }
  footer {
    background: var(--background-button);
    color: var(--color-button);
    padding: 10px;
    user-select: none;
    text-align: center;

    .copyright {
      font-size: max(1.3vw, 0.8em, 0.8rem);
    }
  }
</style>
