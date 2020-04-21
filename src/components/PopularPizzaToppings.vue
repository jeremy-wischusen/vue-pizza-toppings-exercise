<template>
    <v-card>
        <v-card-title>
            Popular Topping Combinations
        </v-card-title>
        <v-card-text>
            <v-row>
                <v-col>
                    <table>
                        <thead>
                            <tr>
                                <th>Rank</th>
                                <th>Topping Combination</th>
                                <th>Times Ordered</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr :key="index" v-for="(item, index) in popularToppings">
                                <td>{{index+1}}</td>
                                <td>{{item.toppings}}</td>
                                <td>{{item.count}}</td>
                            </tr>
                        </tbody>
                    </table>
                </v-col>
            </v-row>
        </v-card-text>
    </v-card>
</template>
<script>
    export default {
        name: 'PopularToppings',
        mounted() {
            const pizzas = require('../pizzas.json');
            let toppingsMap = {};
            let sorted = [];
            for (let p in pizzas) {
                let toppings = pizzas[p].toppings;
                if (toppings.length > 1) {
                    toppings.sort();
                }
                toppings = toppings.toString();
                let map = toppingsMap[toppings];
                if (!map) {
                    toppingsMap[toppings] = 1;
                } else {
                    toppingsMap[toppings]++;
                }
            }
            for (let tc in toppingsMap) {
                let count = toppingsMap[tc];
                sorted.push({
                    count: count,
                    toppings: tc
                });
            }
            sorted.sort((a, b) => {
                if (a.count > b.count) {
                    return -1;
                }
                if (a.count < b.count) {
                    return 1;
                }
                return 0;
            });
            this.popularToppings = sorted.slice(0, 20);
        },
        data: () => ({
            popularToppings: []
        })
    };
</script>
<style scoped>
    table {
        width: 100%;
    }

    th {
        text-align: left;
    }
</style>
