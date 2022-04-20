<template>
    <div id="main-wrapper">
					<div class="wrapper style2">
						<div class="inner">
							<div class="container">
								<div id="content">

									<!-- Content -->

										<article>
											<header class="major">
												<h2>Ma Collection</h2>
											</header>
											<div v-for="(carte,idx) in cartes" :key="idx" class='card-list'>
												<div class='card-title'><b>{{'# '+(idx+1)}}</b> {{carte.name}}</div>
												<div class='card-action'
												@click="goToSelectedCard(carte.id)">👀</div>
											</div>
											

										</article>

								</div>
							</div>
						</div>
					</div>

				</div>
</template>


<script>
import axios from 'axios'

export default {
  name: 'CollectionView',
  components: {
    
  },
  data:()=>({
cartes:[]
  }),
  methods:{
goToSelectedCard(cardId){
	this.$router.push({name:'CardDetails', params:{cardId}})
}
  },
  async created(){
    const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
    this.cartes=lesCartes.data.cards
    
  }
}
</script>

<style scoped>
/* @import url("./assets/css/card-list.css"); */
</style>

