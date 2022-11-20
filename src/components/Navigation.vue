<template>
<header :class="{ 'scrolled-nav': scrollPosition }">
    <nav>
        <div class="branding">
            <img v-bind:src='image' alt="MnM Logo"><!-- div calling the Logo image-->
        </div>

        <ul class="navigation">
            <li><router-link class="link" :to="{ name: 'Home'}">Home</router-link></li><!--list of links in nav bar -->
            <li><router-link class="link" :to="{ name: ''}">About Us</router-link></li>
            <li><router-link class="link" :to="{ name: ''}">Store</router-link></li>
            <li><router-link class="link" :to="{ name: ''}">Contact Us</router-link></li>
        </ul>
        
        
    </nav>
</header>
</template>
      
      <script>
        export default {
      name: 'App',
      components: {
      },

      data() {
        return {
            image: require("D:/App3/hello/src/assets/mm.png"),//returns required image for navbar
            scrollPosition: null,
            windowWidth: null,
        }
      },
      
    }
      </script>
      
<style scoped>/* styling only this component due to scoped attribute*/

    header {
        background-color: rgba(0, 0, 0);
        z-index: 99;
        width: 100%;
        position: fixed;
        transition: .5s ease all;
        color: rgb(255, 0, 0);
    }
    nav {
            position: relative;
            display: flex;
            flex-direction: row;
            padding: 12px 0;
            transition: .5s ease all;
            width: 90%;
            margin: 0 auto;
            @media (max-width: 1140px) {
                max-width: 1140px;
            }
    }
    ul,
        .link {
            font-weight: 500;
            color: rgb(255, 0, 0)fff;
            list-style: none;
            text-decoration: none;

        }
    li {
        text-transform: uppercase;
        padding: 16px;
        margin-left: 16px;

    }

    .link {
        font-size: 14px;
        transition: .5s ease all;
        padding-bottom: 4px;
        border-bottom: 1px solid transparent;
    }
    :hover {
            color: #fff;
            border-color: #fff;
        }
    .branding {
        display: flex;
        align-items: center;

    }
    img {
        width: 50px;
        transition: .5s ease all;
    }
    .navigation {
        display: flex;
        align-items: center;
        flex: 1;
        justify-content: flex-end;
    }

</style>
      