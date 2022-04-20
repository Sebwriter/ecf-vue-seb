<template>
    <div id="header-wrapper">
        <div class="container">

            <!-- Header -->
            <header id="header">
                <div class="inner">

                    <!-- Logo -->
                    <router-link to="/">Magic</router-link>

                    <!-- Nav -->
                    <nav id="nav">
                        <router-link to="/">Home</router-link>
                        <router-link :to="{name:'Collection'}">Ma Collection</router-link>
                    </nav>

                </div>
            </header>

            <!-- Banner -->
            <div id="banner">
                <h2><strong>Magic Card:</strong> Ma collection </h2>
            </div>

        </div>
    </div>
</template>

<script>

export default {
    name:'HeaderView'
}

</script>