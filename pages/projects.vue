<template>
  <div class="projects-container">
    <h1>Moje projekty</h1>
    <div class="list-projects">
      <div v-for="project in projects" class="project-container">
        <div class="name">{{ project.name }}</div>
        <div class="image" @click="showDetails(project)">
          <img :src="project.image" :alt="'project' + project.name" />
        </div>
      </div>
    </div>
    <Transition name="slide-fade">
      <div v-if="details.show === true" class="details">
        <div class="close" @click="details.show = false">X</div>
        <div class="description">
          {{ details.description }}
        </div>
        <div class="languages">
          <div v-for="lang in details.languages" class="lang">
            {{ lang }}
          </div>
        </div>
        <a :href="details.link" class="button">Przejdz na stronę =></a>
      </div>
    </Transition>
  </div>
</template>
<script setup lang="ts">
  useHead({
    title: 'Moje projekty - Igor Ratajczak',
  })
  import picture from '../assets/tim-mccartney-39907.jpg'

  const details = reactive({
    show: ref(false),
    description: ref(''),
    link: ref(''),
    languages: ref<string[]>([]),
  })
  interface Projects {
    name: string
    image: string
    languages: string[]
    link: string
    description: string
  }
  const projects: Projects[] = [
    {
      name: 'Pogoda 2.0',
      image: picture,
      languages: ['Vue', 'CSS'],
      link: '',
      description:
        'Pogoda 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
    },
  ]
  projects.push({
    name: 'Library 2.0',
    image: picture,
    languages: ['Vue', 'HTML'],
    link: '',
    description:
      'Library 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
  })
  projects.push({
    name: 'Biblioteka 2.0',
    image: picture,
    languages: ['Vue', 'HTML'],
    link: '',
    description:
      'Library 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
  })

  const showDetails = (item: Projects) => {
    details.show = true
    details.description = item.description
    details.languages = item.languages
    details.link = item.link
  }
</script>

<style scoped lang="less">
  .slide-fade-enter-active,
  .slide-fade-leave-active {
    transition: all 0.5s ease;
    clip-path: polygon(0% 100%, 100% 100%, 100% 0%, 0px 0px);
  }
  .slide-fade-enter-from,
  .slide-fade-leave-to {
    clip-path: polygon(50% 0%, 50% 100%, 50% 100%, 50% 0%);
    opacity: 0;
  }
  div.projects-container {
    display: flex;
    flex-direction: column;

    div.list-projects {
      display: grid;
      width: 100%;
      height: 100%;
      overflow: auto;
      justify-items: center;
      margin-top: 2em;
      overflow-y: auto;
      margin-bottom: 1em;
      grid-template-columns: repeat(1, 100%);
      grid-template-rows: repeat(1, 15em);
      padding: 10px;

      @media screen and (min-width: 600px) {
        & {
          grid-template-columns: repeat(2, 50%);
          grid-template-rows: repeat(2, 15em);
        }
      }
      @media screen and (min-width: 1100px) {
        & {
          grid-template-columns: repeat(3, 33%);
          grid-template-rows: repeat(3, 15em);
        }
      }
      div.project-container {
        width: 20em;
        height: 100%;
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;

        .name {
          font-size: 2rem;
        }

        .image {
          width: 10em;
          height: 10em;
          border-radius: 50%;
          position: relative;
          cursor: pointer;

          &::before {
            content: 'Więcej...';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background-color: #000000b2;
            opacity: 0;
            transition: opacity 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
          }
          &:hover::before {
            opacity: 1;
          }

          img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: center;
            border-radius: 50%;
          }
        }
      }
    }
    div.details {
      width: 50vw;
      height: 50vh;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: #000000d0;
      padding-top: 4em;
      z-index: 1000;
      box-shadow: 0px 0px 100px 1px white;
      display: grid;
      gap: 2em;

      .close {
        position: absolute;
        top: 0;
        right: 0;
      }

      .languages {
        display: flex;
        gap: 20%;
        justify-content: center;
        grid-row: 2;

        > .lang {
          position: relative;

          &::before {
            content: '';
            width: 10px;
            height: 10px;
            background-color: green;
            border-radius: 50px;
            position: absolute;
            top: 50%;
            left: -50%;
            transform: translate(0%, -50%);
          }
        }
      }
      .description {
        position: relative;
        grid-row: 1;
        grid-column: 1;
        text-align: center;
        align-content: center;
        transition: opacity 0.5s ease;
      }
      .button {
        width: max-content;
        height: max-content;
        padding: 1em;
        border-radius: 50px;
        background: linear-gradient(to left, green, darkgreen);
        color: white;
        text-decoration: none;
        justify-self: center;
      }
    }
  }
</style>
