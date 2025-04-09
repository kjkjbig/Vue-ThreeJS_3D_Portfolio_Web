<template>
  <div class="navbar">
    <navb @change-section="(name) => handleSection(name)" />
  </div>

  <hr style="height:2px;border-width:0;background-color:gray" />

  <HeroSection ref="heroRef" />

  <Contact v-if="showContact" @close="showContact = false" />

  <Transition name="slide" mode="out-in">
    <component :is="currentSection" />
  </Transition>
</template>


<script setup>
  import { ref } from 'vue'
  import HeroSection from '../components/HeroSection.vue'
  import navb from '../components/navb.vue'
  import Hello from '../components/Hello.vue'
  import about from '../components/about.vue'
  import Skills from '../components/skills.vue'
  import Project from '../components/project.vue'
  import Contact from '../components/Contact.vue'

  const heroRef = ref(HeroSection)

  const components = {
    Hello,
    about,
    Skills,
    Project,
    Contact
  }

  const showContact = ref(false)

  const currentSection = ref(Hello)

  function handleSection(name) {
    if (name !== 'Contact') {
      showContact.value = false
      currentSection.value = components[name]
    }

    if (heroRef.value) {
      switch (name) {
        case 'Hello': heroRef.value.movecam(2); break;
        case 'about': heroRef.value.movecam(-10); break;
        case 'Skills': heroRef.value.movecam(-20); break;
        case 'Project': heroRef.value.movecam(-30); break;
      }
    }

    if (name === 'Contact') {
      showContact.value = true
    }
  }


</script>

<style scoped>
  /* .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s ease;
  }
  .fade-enter-from, .fade-leave-to {
    opacity: 0;
  } */
  .slide-enter-active, .slide-leave-active {
  transition: all 0.5s ease;
  }
  .slide-enter-from {
    opacity: 0;
    transform: translateY(50px);
  }
  .slide-leave-to {
    opacity: 0;
    transform: translateY(-50px);
  }
  .navbar{
    display: flex;
    justify-content:center;
    align-items: center;
  }

</style>
