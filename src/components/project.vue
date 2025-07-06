<template>
    <div class="pj">
      
      <div
        v-for="(box, index) in boxes"
        :key="index"
        :class="`box${index + 1}`"
      >
        <button @click="box.visible = !box.visible">
          {{ box.title }}
        </button>
  
        <transition name="fade">
            <div :class="`content${index + 1}`" v-show="box.visible">
            <template v-for="(item, i) in box.items" :key="`item-${index}-${i}`">
                <li
                    v-if="!item.link"
                    :class="item.class"
                    @click="item.popupImages ? openPopup(item.popupImages) : null"
                >
                    {{ item.text }}
                </li>

                <li v-else>
                    <a
                    :href="item.link"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="link-item"
                    >
                    {{ item.text }}
                    </a>
                </li>
            </template>

          </div>
        </transition>
      </div>
  
      <!-- Popup -->
      <div class="image" v-if="popupImages.length">
        <div class="popup">
          <button class="close-btn" @click="popupImages = []">×</button>
          <img
            v-for="(src, i) in popupImages"
            :key="i"
            :src="src"
            class="popup-img"
          />
        </div>
      </div>
    </div>
  </template>
  
  
  
<script setup>
    import { ref } from 'vue'

    
    import icpc1 from '../assets/icpc1.jpg'
    import icpc2 from '../assets/icpc2.jpg'

    
    import tensei1 from '../assets/tensei1.png'
    import tensei2 from '../assets/tensei2.png'

    const popupImages = ref([])

    function openPopup(images) {
    popupImages.value = images
    }

    const boxes = ref([
    {
        title: 'Experience ⮜',
        visible: false,
        items: [
        {
            text: 'Participate in the ICPC 2024 competition ⮜',
            class: 'icpc',
            popupImages: [icpc1, icpc2] 
        },
        {
            text: 'Participate in the development of the Roblox Tensei Magic ⮜',
            class: 'tensei',
            popupImages: [tensei1, tensei2] 
        }
        ]
    },
    {
        title: 'Projects ⮜',
        visible: false,
        items: [
        { 
            text: 'GITHUB ⮜',
            link: 'https://github.com/kjkjbig'
        },
        { 
            text: '3D Portfolio ⮜' , 
            link: 'https://discord.gg/XBjpWMmexx'
        },
        { 
            text: 'Roblox Obby Game ⮜',
            link: 'https://www.roblox.com/games/18171925836/Be-the-obby-master-UPD-1-0'
        }
        ]
    },
    {
        title: 'Other ⮜',
        visible: false,
        items: [
        { 
            text: 'Content creation ⮜',
            link: 'https://www.youtube.com/@Bcoding-65'
        },
        ]
    }
    ])
</script>

<style scoped>
    .pj {
        position: relative;
        text-align: center;
        color: white;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        flex-wrap: wrap;
        gap: 2rem;
        margin-top: 10vh;
    }

    [class^='box'] {
        font-size: 1.5rem;
        border-radius: 15px;
        padding: 2vmax;
        width: 300px;
    }

    [class^='content'] {
        background-color: rgba(94, 94, 94, 0.76);
        text-align: left;
        border-radius: 15px;
        padding: 5%;
        line-height: 1.5;
    }

    button {
        background: none;
        border: none;
        font-size: 2rem;
        color: lightblue;
        font-weight: bold;
        transition: all 0.3s ease;
        margin-bottom: 2.5vh;
    }

    button:hover {
        font-size: 2.2rem;
        cursor: pointer;
    }

    li {
        font-size: 1.25rem;
        transition: all 0.3s ease;
    }

    li:hover {
        cursor: pointer;
        color: gold;
    }

    .image {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.75);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 999;
    }

    .popup {
        position: relative;
        background: #222;
        padding: 2rem;
        border-radius: 12px;
        box-shadow: 0 0 20px #000;
        text-align: center;
        max-width: 90vw;
        max-height: 90vh;
        overflow: auto;
    }

    .popup-img {
        width: 400px;
        max-width: 100%;
        margin: 1rem;
        border-radius: 15px;
    }

    .close-btn {
        position: absolute;
        top: 10px;
        right: 15px;
        background: none;
        border: none;
        font-size: 2rem;
        color: white;
        cursor: pointer;
        transition: 0.2s;
    }

    .link-item {
        color: white;
        text-decoration: none;
        font-size: 1.25rem;
        transition: all 0.3s ease;
        display: inline-block;
    }

    .link-item:hover {
        color: gold;
        text-decoration: underline;
        cursor: pointer;
    }


    .close-btn:hover {
    color: red;
    }

    .fade-enter-active,
    .fade-leave-active {
    transition: all 0.3s ease;
    }

    .fade-enter-from,
    .fade-leave-to {
    opacity: 0;
    transform: translateY(-10px);
    }

</style>