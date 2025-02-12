<template>
    <header>
        <nav class="container">
            <div class="branding">
                <img src="../assets/balls_light_glass_neon.jpg" alt="">
                <h1>Todo App</h1>
            </div>
            <ul class="nav-routes">
                <router-link to="/" :class="{ active: activeRoute === 'home' }">Home</router-link>
                <router-link :to="{ name: 'about' }" :class="{ active: activeRoute === 'about' }">About</router-link>
            </ul>
        </nav>
    </header>
</template>

<script>
import { ref, watch } from 'vue';
import { useRoute } from 'vue-router';

export default {
    setup() {
        const route = useRoute();
        const activeRoute = ref(route.name);

        watch(
            () => route.name,
            (newRouteName) => {
                activeRoute.value = newRouteName;
            }
        );


        return { activeRoute }
    }
}
</script>

<style lang="scss" scoped>
header {
    background-color: #f1f1f1;

    nav {
        display: flex;
        align-items: center;
        padding: 25px 16px;

        .branding {
            display: flex;
            align-items: center;
            gap: 8px;

            img {
                max-width: 70px;
                border-radius: 20px;
            }

            h1 {
                font-size: 24px;
            }
        }

        .nav-routes {
            display: flex;
            flex: 1;
            justify-content: flex-end;
            align-items: center;
            gap: 12px;
            list-style: none;

            a {
                text-decoration: none;
                color: inherit;
            }

            a:hover {
                color: #41b080;
            }

            .active {
                color: #41b080;
                padding: 8px;
                border-bottom: 3px solid #41b080;
            }

        }

    }
}
</style>