<template>
    <div class="sk">

        <h1 class="s1">Skills</h1>
        
        <div class="box1">
            <h2>Programming languages</h2>
            <ul>
                <li>Python</li>
                <li>Java</li>
                <li>C#</li>
                <li>Lua</li>
                <li>Javascript</li>
                <li>HTML/CSS</li>
            </ul>
            <h2>Frameworks & Libraries</h2>
            <ul>
                <li>Vue.js</li>
                <li>TailwindCSS</li>
                <li>Bootstrap</li>
                <li>Three.js</li>
                <li>React</li>
            </ul>
        </div>

        <h1 class="s2">Skills</h1>

        <div class="box2"> 
            <h2>Tools & Technologies</h2>
            <ul>
                <li>Blender (3D modeling)</li>
                <li>Git/GitHub</li>
                <li>Canva (Graphic Design)</li>
            </ul>
            <h2>Others</h2>
            <ul>
                <li>Game Development</li>
                <li>AI/Deep Learning (YOLO)</li>
                <li>Web Development</li>
                <li>Content Creation (<a href="https://www.youtube.com/@Bcoding-65">Bcoding</a>)</li>
            </ul>
        </div>
    </div>
</template>

<script setup>

</script>

<style scoped>

    a{
        text-decoration: none;
        color:lightblue;
    }

    a:hover{
        color: black;
    }

    .s1{
        display: none;
    }

    .s2{
        text-align: center;
        color: white;
        margin-top: 5vh;
        font-size: 3rem;
        text-shadow: 2px 2px 8px #353535;
    }

    .sk{
        display: flex;
        text-align: center;
        color: white;
        flex-direction: row;
        justify-content: center;
    }

    .box1{
        background-color: rgba(102, 102, 102, 0.836);
        font-size: 1.5rem;
        margin-top: 15vh;
        border-radius: 15px;
        padding: 2vmax;
        box-shadow: 2px 2px 8px #353535;
        margin-left: 10%;
        text-align: left;
        justify-content: center;
    }

    .box2{
        background-color: rgba(102, 102, 102, 0.836);
        font-size: 1.5rem;
        margin-top: 15vh;
        border-radius: 15px;
        padding: 2vmax;
        box-shadow: 2px 2px 8px #353535;
        margin-right: 10%;
        text-align: left;
    }

    @media only screen and (max-width: 600px) {

        .sk{
            display: block;
            text-align: center;
            color: white;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            
        }

        .s2{
            display: none;
        }

        .s1{
            display: block;
            text-align: center;
            color: white;
            font-size: 1.5rem;
            text-shadow: 2px 2px 8px #353535;
        }

        .box1{
            margin: 0 0 0 0;
            background-color: rgba(102, 102, 102, 0.836);
            font-size: 0.8rem;
            line-height: 1;
            margin: 0 20% 20px 20%;
        }   

        .box2{
            margin: 0 0 0 0;
            background-color: rgba(102, 102, 102, 0.836);
            font-size: 0.8rem;
            line-height: 1;margin: 0 20% 0 20%;
        }   

    }
</style>