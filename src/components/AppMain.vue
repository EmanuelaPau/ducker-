<template>
    <main class="d-flex justify-content-center p-5">
        <div class="game-container col-lg-6 col-12 p-5">
            <h1>Ducker</h1>
            <div class="d-flex justify-content-between w-100">
                <h3>Time</h3>
                <h3>00015</h3>
            </div>
            <div class="game-box d-flex flex-wrap justify-content-center">
                <!-- <div v-for="i in 81" class="square" :class="i % 2 === 0 ?  'grey-square' : '' "> -->
                    <div class="row" v-for="row,rowIndex in gridMatrix">
                        <div v-for="cell,cellIndex in row" class="square" :class="cell=== '' ? '' : cell, (rowIndex % 2 === 0 && cellIndex % 2 === 0) || (rowIndex % 2 !== 0 && cellIndex % 2 !== 0) ? 'darksquare' : '' " ></div>
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
    // height: 100vh;

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
            .row {
                width: 100%;

                .square {
                    width: calc(100% / 9);
                    aspect-ratio: 1/1;
                    border: 1px dotted #a4bbcc;
                    cursor: pointer;
                    /* border: 1px dashed black; */

                    /* 👇 Aggiunta */
                    background-size: contain;
                }

                .darksquare {
                    background-color: #d4ecff;
                }

                .river {
	                background-color: lightskyblue;
                }

                .road {
                    border-top: 1px dashed white;
                    border-bottom: 1px dashed white;
                    background-color: gray;
                }

                .wood {
                    background-image: url('../../public/wood.png');
                    background-color: lightskyblue;
                }

                .bus {
                    background-image: url('../../public/bus.png');
                    border-top: 1px dashed white;
                    border-bottom: 1px dashed white;
                    background-color: gray;
                }

                .car {
                    background-image: url('../../public/car.png');
                    border-top: 1px dashed white;
                    border-bottom: 1px dashed white;
                    background-color: gray;
                }

                .duck {
                    background-image: url('../../public/duck-walk.gif');
                }

                .duck-arrived {
                    background-image: url('../../public/duck-standing.png');
                }

                .duck-drowned {
                    background-image: url('../../public/duck-drowned.png');
                }
                .duck-hit {
                    background-image: url('../../public/duck-hit.png');
                }

                .river.duck {
                    background-image: url('../../public/duck-walk.gif'), url('../../public/wood.png');
                }

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
            // 0 cella vuota, 1 blocco 
            gridMatrix: [
                ['', '', '', '', '', '', '', '', ''],
                ['river', 'wood', 'wood', 'river', 'wood', 'river', 'river', 'river', 'river'],
                ['river', 'river', 'river', 'wood', 'wood', 'river', 'wood', 'wood', 'river'],
                ['', '', '', '', '', '', '', '', ''],
                ['road', 'bus', 'road', 'road', 'road', 'car', 'road', 'road', 'road'],
                ['road', 'road', 'road', 'car', 'road', 'road', 'road', 'road', 'bus'],
                ['road', 'road', 'car', 'road', 'road', 'road', 'bus', 'road', 'road'],
                ['', '', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', '', '']
            ],
            
            // Informazioni utili alla logica di gioco
            victoryRow: 0,
            riverRows: [1, 2],
            roadRows: [4, 5, 6],
            duckPosition: { y: 8, x: 4 },
            contentBeforeDuck: '',
            time : 15,
            isGameOver : false,
        }
    },
    methods: {

    },
}		
</script>
