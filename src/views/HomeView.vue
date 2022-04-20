<template>
  <div id="main-wrapper">
			<div class="wrapper style1">
				<div class="inner">

					<!-- Feature 1 -->
					<section class="container box feature1">
						<div class="row">
							<div class="col-12">
								<header class="first major">
									<h2>Mes 3 Dernières Cartes</h2>
								</header>
							</div>
							<div class="col-4 col-12-medium">
								<section>
									<a href="#" class="image featured"><img :src="cartes[cartes.length-1].imageUrl" alt="" /></a>
									<header class="second icon solid fa-dragon">
										<h3>{{cartes[cartes.length-1].name}}</h3>
										<p>{{cartes[cartes.length-1].originalType}}</p>
									</header>
								</section>
							</div>
							<!--Il peut y avoir un soucis d'affichage car la carte à l'index 98 ne contient pas toutes les infos
							Mais le code permet de bien afficher les 3 dernières cartes ajoutées à la liste/ au tableau-->
							<div class="col-4 col-12-medium">
								<section>
									<a href="#" class="image featured"><img :src="cartes[cartes.length-2].imageUrl" alt="" /></a>
									<header class="second icon solid fa-dragon">
										<h3>{{cartes[cartes.length-2].name}}</h3>
										<p>{{cartes[cartes.length-2].originalType}}</p>
									</header>
								</section>
							</div>
              <div class="col-4 col-12-medium">
								<section>
									<a href="#" class="image featured"><img :src="cartes[cartes.length-3].imageUrl" alt="" /></a>
									<header class="second icon solid fa-dragon">
										<h3>{{cartes[cartes.length-3].name}}</h3>
										<p>{{cartes[cartes.length-3].originalType}}</p>
									</header>
								</section>
							</div>

						</div>
					</section>

				</div>
			</div>
		</div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
    
  },
  data:()=>({
cartes:[]
  }),
  async created(){
    const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
    this.cartes=lesCartes.data.cards
    console.log(this.cartes)
    console.log(this.cartes.length)
  }
}
</script>
