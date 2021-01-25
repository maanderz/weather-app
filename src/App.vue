<template>
	<div>
		<h1>Weather App</h1>
		<div class="container">
			<div class="row">
				<input v-model="city" placeholder="Enter a city (no abbreviations please!)">
				<button class="search-btn" @click="submit"> 
					<img class="button-size" src="./assets/search.png" />
				</button>
			</div> 
		</div>
		<div class="row-1">
			{{ response }}
		</div> 
	</div>
</template>

<script>
import axios from 'axios';
export default {
	name: 'App',
	data(){
		return {
			city: '',
			response: ''
		}
	},
	methods: {
		submit(){
			axios.get(`http://localhost:3001/`, {
				params: {
					city: this.city
				}
			})
			.then((response) => {
				this.response = response;
			})
		}
	}
}
</script>

<style>
#app {
	margin: 0 auto;
	width: 95%;
	@media (min-width: 600px) {
		width: 75%;
	}
	@media (min-width: 900px) {
		width: 65%;
	}
	position: relative;
}
h1 {
	font-size: 75px;
	margin: 50px 0;
	text-align: center;
}
body {
	background: #455a64;
	color: #FFFFFF;
}
input {
	background: transparent;
	border: none;
	border-bottom: 1px solid white;
	font-size: 30px;
	height: 50px;
	padding-bottom: 15px;
	text-align: center;
	color: white;
	width: 75%;
}
input:focus {
	outline: 0;
}
.row {
	display: flex; 
	justify-content: center;
    align-items: center;
}
.row-1 {
	font-size: 30px;
	position: absolute;
    top: 60%;
    left: 50%;
    transform: translate(-50%, -50%);
}
.search-btn {
	background: #455a65;
	border: none; 
	padding: 1rem;
}
.button-size {
    height: 35px;
    width: 35px;
}
</style>
