<template>
  <div class="project-container">
    <h1>Moje projekty</h1>
    <div class="list-projects">
      <div v-for="project in projects" class="project">
        <div class="name">{{ project.name }}</div>
        <div class="image">
          <img :src="project.image" :alt="'project' + project.name" />
        </div>
        <div class="languages">
          <div v-for="lang in project.languages" class="lang">{{ lang }}</div>
        </div>
        <div class="description">
          {{ project.description }}
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
  useHead({
    title: 'Moje projekty - Igor Ratajczak',
  })
  import picture from '../assets/tim-mccartney-39907.jpg'

  interface Projects {
    name: string
    image: string
    languages: Array<string>
    description: string
  }
  const projects: Projects[] = [
    {
      name: 'Pogoda 2.0',
      image: picture,
      languages: ['Vue', 'CSS'],
      description:
        'Pogoda 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
    },
  ]
  projects.push({
    name: 'Library 2.0',
    image: picture,
    languages: ['Vue', 'HTML'],
    description:
      'Library 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
  })
  projects.push({
    name: 'Library 2.0',
    image: picture,
    languages: ['Vue', 'HTML'],
    description:
      'Library 2.0 pomoże ci sprawdzic pogodę na najbliższe dni w prosty i szybki sposób.',
  })
</script>

<style scoped lang="less">
  div.project-container {
    display: flex;
    flex-direction: column;
  }
  div.list-projects {
    display: grid;
    width: 100%;
    height: 100%;
    overflow: auto;
    justify-items: center;
    margin-top: 2em;
    gap: 2em;
    overflow-y: auto;
    margin-bottom: 1em;
    grid-template-columns: repeat(1, 1fr);
    padding: 10px;

    @media screen and (min-width: 600px) {
      & {
        grid-template-columns: repeat(2, 1fr);
      }
    }
    @media screen and (min-width: 1100px) {
      & {
        grid-template-columns: repeat(3, 1fr);
      }
    }

    div.project {
      border-radius: 15px;
      background-color: rgba(134, 138, 134, 0.856);
      display: grid;
      grid-template: 2em calc(100% - 4em - 20px) 2em / 100%;
      width: 100%;
      gap: 10px;

      .name {
        font-size: 2rem;
        grid-row: 1;
      }
      .image {
        grid-row: 2;
        grid-column: 1;

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          object-position: center;
        }
      }
      .languages {
        display: flex;
        gap: 20%;
        justify-content: center;
        grid-row: 3;

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
        grid-row: 2;
        grid-column: 1;
        opacity: 0;
        background: #000000ad;
        text-align: center;
        align-content: center;
        transition: opacity 0.5s ease;

        &:hover {
          opacity: 1;
        }
      }
    }
  }
</style>
