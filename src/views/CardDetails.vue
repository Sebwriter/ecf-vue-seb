<template>
    <div id="main-wrapper">
        <div class="wrapper style2">
            <div class="inner">
                <div class="container">
                    <div class="row">
                        <div class="col-8 col-12-medium">
                            <div id="content">

                                <!-- Content -->

                                <article>
                                    <header class="major">
                                        <h2>{{ carte.name }}</h2>
                                        <p>{{ carte.artist }}</p>
                                    </header>

                                    <span class="image featured">
                                        <img :src="carte.imageUrl" alt="" />
                                    </span>

                                    <!-- au cas où l'image serait manquante -->
                                    <h4 style="width:50%; margin-left:25%; margin-bottom:10px" v-if="!carte.imageUrl">
                                        Sorry, our wizards are purchasing this image !
                                    </h4>
                                    <h4 style="width:50%; margin-left:25%; margin-bottom:40px" v-if="!carte.imageUrl">
                                        Please excuse us for the incident !
                                    </h4>

                                    <p>{{ carte.text }}</p>
                                </article>

                            </div>
                        </div>
                        <div class="col-4 col-12-medium">
                            <div id="sidebar">

                                <!-- Sidebar -->

                                <section>
                                    <header class="major">
                                        <h2>Infos</h2>
                                    </header>
                                    <p>set name: <b>{{ carte.setName }}</b></p>
                                    <p>rarity: <b>{{ carte.rarity }}</b></p>
                                    <p>toughness: <b>{{ carte.toughness }}</b></p>

                                    <span class="button alt icon ">
                                        {{ 'Card power : ' + power }}

                                    </span>
                                </section>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'CardDetails',
    components: {

    },

    data: () => ({
        carte: {},
        power: ""
    }),
    async created() {
        const { cardId } = this.$route.params
        const laCarte = await axios.get('https://api.magicthegathering.io/v1/cards/' + cardId)
        this.carte = laCarte.data.card
        //console.log(this.carte)

        for (let i = 0; i < laCarte.data.card.power; i++) {
            this.power = this.power + "🔥"
        }
        if (this.power == "") { this.power = "None" }
    }
}
</script>

<style scoped >

</style>