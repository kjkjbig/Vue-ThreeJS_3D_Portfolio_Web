<template>
    <div class="ab">
        <h1 class="">About me</h1>
        <p class="">
                I'm a third-year Computer Science student at Rajamangala University of Technology Krungthep.
            I love exploring and experimenting with different things — from websites and games to 3D models and digital content.
            I've been passionate about coding since high school and also enjoy using my creativity. I have fun turning new ideas into real projects, whether it's a Roblox game, a personal portfolio, or something entirely different.
            My goal is to keep learning across different areas and combine everything I know to create something truly awesome.
        </p>
        <div style="margin-top: 10%;">
            <h3>This website is using <img src="../assets/vue.svg" style="width: 50px; height: 50px;"> + <img src="../assets/three-js-icon.svg" style="width: 50px; height: 50px;"></h3>
        </div>
    </div>
</template>

<script setup>
    

</script>

<style scoped>

    .ab{
        width: 40%;
        margin-top: 7vh;
        margin-left: 10vw;
        text-align: left;
        color: white;
        line-height: 1.5;
        text-shadow: 2px 2px 8px #353535;
    }

    h1{
        font-size: 3rem;
    }

    p{
        border-radius: 15px;
        background-color: rgba(94, 94, 94, 0.76);
        padding: 2vmax;
        font-size: 1.3rem;
        box-shadow: 2px 2px 8px #353535;
    }


    @media only screen and (max-width: 600px) {
        .ab{
            width: 60%;
            margin-top: 7vh;
            margin-left: 10vw;
            text-align: left;
            color: white;
            line-height: 1;
            text-shadow: 2px 2px 8px #353535;
        }

        h1{
            font-size: 2rem;
        }

        p{
            border-radius: 15px;
            background-color: rgba(94, 94, 94, 0.76);
            padding: 3vmax;
            font-size: 1rem;
            box-shadow: 2px 2px 8px #353535;
        }

        h3{
            font-size: 1rem;
        }
    }

</style>