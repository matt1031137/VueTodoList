<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <header>
        <nav class="container">
            <div class="branding">
                <img src="../assets/Vue_Logo_Black.png" alt="">
                <h1>Vue 待辦清單</h1>
            </div>
            <ul class="nav-routes">
                <RouterLink to="/">首頁</RouterLink>
                <RouterLink to="/about">關於</RouterLink>
            </ul>
        </nav>
    </header>
</template>


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
                max-width: 50px;
            }

            h1 {
                font-size: 24px;
            }
        }

        .nav-routes {
            display: flex;
            flex: 1;
            justify-content: flex-end;
            gap: 12px;
            list-style: none;

            a {
                text-decoration: none;
                color: inherit;
            }
        }
    }
}
</style>