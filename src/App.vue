<template>

	<header>
		<nav class="hero is-light">
			<img class="container image is-128x128" src="./assets/logo.png">
		</nav>

	</header>

	<main>
		<section class="section">
			<div class="title">Username Generator</div>
			<h5 class="title is-5">Create alternative username options for if yours is taken</h5>
			<div class="field">
			<input class="input  is-rounded column is-one-third" 
				type="text" 
				placeholder="Please input your username" 
				v-model="this.name" 
				@keyup.enter="this.nameGen(this.name, this.additions)">
			</div>
			<button class="level-right button is-rounded is-primary" @click="this.nameGen(this.name, this.additions)">
				Generate Alternatives
			</button>
			<div class="tile is-vertical is-light">
				<CopyButton v-for="item in this.newNames" :text=item />
			</div>
		</section>
	</main>


	<!-- <section class="section is-large"></section> -->
	<footer class="footer">
		<div class="content has-text-centered">
		<p><strong>copyright © 2023</strong></p>
		<p>Thank you for using the username generator :)</p>
		</div>
	</footer>
	
	</template>

	<script>

	import CopyButton from './components/CopyButton.vue'

	export default {
		name: 'App',
		components: {
		CopyButton
		},
		data(){
		return {
			name: '',
			additions: ['.','-','_','.-','._','-.','-_','_.','_-'],
			newNames: [],
		}
		},
		methods: {		
		nameGen(name, additions){
			if (name === '') {
				this.newNames = []
			} else {
				this.newNames = []
				additions.forEach((item) => {
				let newName1 = name.concat(item)
				let newName2 = item.concat(name)
				this.newNames = [...this.newNames, newName1, newName2]
				})
			}
		}
		}
	}
	</script>
