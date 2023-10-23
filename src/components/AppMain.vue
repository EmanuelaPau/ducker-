<template>
    <main class="d-flex justify-content-center p-5">
        <div class="game-container col-lg-6 col-12 p-5">
            <h1>Ducker</h1>
            <div class="d-flex justify-content-between w-100">
                <h3>Time</h3>
                <h3>00015</h3>
            </div>
            <div class="game-box d-flex flex-wrap">
                <div v-for="i in 81" class="square" :class="i % 2 === 0 ?  'grey-square' : '' ">
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use '../styles/partials/_variables.scss';
@use '../styles/partials/_mixins.scss';

main {
    background-color: #001531;
    width: 100vw;
    height: 100vh;

    .game-container {
        // background-color: aqua;
        h1 {
            color: #00e165;
            font-weight: 800;
            font-size: 3rem;
        }
        h3 {
            font-weight: 600;
            color: #eaf6ff;
        }

        .game-box {
            background-color: #eaf6ff;
            border: 2px solid black;

            .square {
                width: calc(100% / 9);
                aspect-ratio: 1/1;
            }

            .grey-square {
                width: calc(100% / 9);
                aspect-ratio: 1/1;
                background-color: #b6cddf;
            }
        }
    }
}

</style> 


<script>
export default {
    name: 'AppMain',
    components: {
    },
    data() {
        return {
           
        }
    },
    methods: {
    },
}		
</script>
