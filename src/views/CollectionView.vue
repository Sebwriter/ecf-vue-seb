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
												@click="goToSelectedCard(carte.id)"
												@mouseover="pointer()">👀</div>
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
},
 pointer() {
            const mesYeux = document.querySelectorAll('.card-action')
            for (let i = 0; i < mesYeux.length; i++) {
                mesYeux[i].style.cursor = 'pointer'
            }
        }
  },
  async created(){
    const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
    this.cartes=lesCartes.data.cards
    
  }
}
</script>

<style scoped>
div.card-list{
    border-radius:8px;
    padding:8px;
    border:1px solid grey;
    display: flex;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
    margin-bottom:4px;
}

div.card-title{
    flex:6
}

div.card-action{
    flex:1
}
div.card-action a{
    outline: none;
    text-decoration: none;
}
</style>

