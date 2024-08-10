<template>
  <div>
    <header>
      <div class="logo">LOGO</div>

      <div class="navbar" :class="showMenu ? 'open' : 'hide'">
        <div class="close" @click="showMenu = false">X</div>
        <NuxtLink to="/" @click="showMenu = false"
          ><div class="item">
            <b>Strona główna</b>
          </div>
        </NuxtLink>
        <NuxtLink to="/projects" @click="showMenu = false"
          ><div class="item">
            <b>Moje projekty</b>
          </div>
        </NuxtLink>
        <NuxtLink to="/about" @click="showMenu = false"
          ><div class="item">
            <b>O mnie</b>
          </div>
        </NuxtLink>
      </div>
      <div class="menu-mobile" @click="showMenu = true">
        <svg width="40" height="40" viewBox="0 0 100 100">
          <line
            x1="0"
            y1="28"
            x2="100"
            y2="28"
            stroke="white"
            stroke-width="5"
          />
          <line
            x1="0"
            y1="56"
            x2="100"
            y2="56"
            stroke="white"
            stroke-width="5"
          />
          <line
            x1="0"
            y1="84"
            x2="100"
            y2="84"
            stroke="white"
            stroke-width="5"
          />
        </svg>
      </div>
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
  const showMenu = ref(false)

  window.addEventListener('resize', () => {
    if (window.innerWidth > 1000) showMenu.value = false
  })
</script>

<style lang="less">
  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;
    background: linear-gradient(to left, rgb(0, 65, 0), rgb(0, 138, 0));
    color: white;
    padding: 10px;
    user-select: none;

    > .logo {
      flex-grow: 1;
    }

    .navbar {
      flex-grow: 10;
      display: flex;
      gap: 2em;
      justify-content: center;

      .close {
        display: none;
      }

      > a {
        color: white;
        text-decoration: none;

        .item {
          border: 2px solid white;
          border-radius: 25px;
          padding: 0.5em 1em;

          &:hover {
            background-color: rgba(255, 255, 255, 0.267);
          }
        }
      }
      @media (max-width: 1000px) {
        flex-direction: column;
        position: absolute;
        top: 0;
        right: 0;
        width: 50vw;
        height: 100vh;
        justify-content: baseline;
        background-color: rgba(0, 0, 0, 0.904);
        padding: 2em;

        &.hide {
          display: none;
        }

        &.open {
          display: flex;
        }

        .close {
          display: block;
        }
        .item {
          background: linear-gradient(to right, rgb(0, 65, 0), rgb(0, 138, 0));
        }
      }
    }
    .menu-mobile {
      display: none;

      @media (max-width: 1000px) {
        display: block;
      }
    }
  }
  main {
    width: 100vw;
    height: 100%;
    text-align: center;
  }
  footer {
    background: linear-gradient(to left, rgb(0, 65, 0), rgb(0, 138, 0));
    color: white;
    padding: 10px;
    user-select: none;
    text-align: center;

    .copyright {
      font-size: max(1.3vw, 0.8em, 0.8rem);
    }
  }
</style>
