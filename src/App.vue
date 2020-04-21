<template>
    <v-app>
        <v-content>
            <PopularToppings/>
        </v-content>
    </v-app>
</template>
<script>
    import PopularToppings from './components/PopularPizzaToppings';

    export default {
        name: 'App',
        components: {
            PopularToppings
        }
    };
</script>
