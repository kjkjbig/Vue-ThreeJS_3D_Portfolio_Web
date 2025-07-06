<template>
    <div class="popup">
      <div class="box">
        <button class="close-btn" @click="$emit('close')">×</button>
        <img src="../assets/tmbn.jpg">
        <h2>Email : natkamol_03@hotmail.com</h2>
        <h2>Git : <a href="https://github.com/kjkjbig">https://github.com/kjkjbig</a></h2>
        <h2>LineID : susmanjojometal12345</h2>
        <h2>Phone : 082-215-1534</h2>
      </div>
    </div>
</template>
  
<script setup>
  defineEmits(['close'])
</script>
  
<style scoped>

    img{
        border-radius: 50%;
        width: 50%;
        border: 3px solid white;
    }

    a{
        text-decoration: none;
        color: lightblue;
    }

    a:hover{
        color:black;
    }

    .popup {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 999;
    }
  
    .box {
        background-color: #333;
        color: white;
        padding: 3rem;
        border-radius: 20px;
        box-shadow: 0 0 20px black;
        text-align: center;
        max-width: 400px;
    }
  
    .close-btn {
        position: absolute;
        top: 10px;
        right: 20px;
        background: none;
        border: none;
        font-size: 2rem;
        color: white;
        cursor: pointer;
        transition: 0.2s;
    }
  
    .close-btn:hover {
        color: red;
    }
</style>
  