<template>
	<v-responsive class="mx-auto mt-5 loginPage">
		<v-container grid-list-md>
			<v-layout row>
				<v-flex text-xs-center xs12 md12>
					<v-toolbar-title>
						<h2 class="display-2 font-weight-light blue-grey--text text--darken-4 text-sm-center">{{ title }}</h2>
					</v-toolbar-title>
				</v-flex>
			</v-layout>
			<v-card
			class="mx-auto mt-5 pt-4 pb-2 black--text card-principal"
			color="white lighten-1"
			elevation=12
			>
			<v-layout row>
				<v-flex text-xs-center xs12 md12>
					<v-card-text>
						<LvLogin />
					</v-card-text>
				</v-flex>
			</v-layout>
			<!-- Buttons and Card's -->
			<v-layout align-center row>
				<v-flex text-xs-center xs6 md6>
					<v-btn flat color="secondary" @click="dialogRegister = !dialogRegister">Cadastro</v-btn>
				</v-flex>
				<v-flex text-xs-center xs6 md6>
					<v-btn flat color="secondary" @click="dialogPass = !dialogPass">Esqueci a senha</v-btn>
				</v-flex>
			</v-layout>
			<!-- <v-dialog v-model="dialogPass" max-width="400px">
				<v-card class="mx-auto pt-4 pb-2 black--text card-pass" color="white lighten-1" elevation=12>
					<h3>Implementar</h3>
				</v-card>
			</v-dialog> -->
			<v-dialog v-model="dialogRegister" max-width="600px">
				<v-card class="mx-auto px-3 pt-4 pb-3 black--tex card-register" color="white lighten-1" elevation=12>
					<LvRegister v-on:registered="close"/>
				</v-card>
			</v-dialog>
		</v-card>
	</v-container>
</v-responsive>
</template>

<script>
import LvLogin from '@/components/LvLogin.vue'
import LvRegister from '@/components/LvRegister.vue'

export default{
	data() {
		return {
			title: "Bem vindo(a) ao SIGAA de Araque",
			dialogPass: false,
			dialogRegister: false,
		}
	},
	methods: {
		//Método utilizado para manipular o diálogo de cadastro
		close (){
			this.dialogRegister = false
		}
	},
	components: {LvLogin, LvRegister},
}
</script>

<style>
.card-principal {
	max-width: 400px;
	margin: auto;
}
.card-home {
	max-width: 1000px;
	margin: auto;
}
.card-pass {
	max-width: 400px;
	margin: auto;
}
.card-register {
	max-width: 600px;
	margin: auto;
}
.borda {
	border: 1px solid red;
}
</style>