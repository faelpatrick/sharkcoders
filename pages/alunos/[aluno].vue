<template>
	<v-app>
		<v-main class="bg-black text-white">
			<v-container>
				<h1 class="text-h5 mb-4" style="color: #8f88ba;">
					Projetos de {{ nomeAluno }}
				</h1>

				<v-row v-if="projetos.length">
					<v-col v-for="(projeto, index) in projetos" :key="index" cols="12" md="6">
						<v-card :href="projeto.link" target="_blank" color="#8f88ba" dark>
							<v-card-title>{{ projeto.titulo }}</v-card-title>
						</v-card>
					</v-col>
				</v-row>

				<v-alert v-else type="info" text>
					Ainda não há projetos cadastrados para este aluno.
				</v-alert>
			</v-container>
		</v-main>
	</v-app>
</template>

<script setup>
const route = useRoute()

const deslugify = (slug) =>
	slug
		.split('-')
		.map((s) => s.charAt(0).toUpperCase() + s.slice(1))
		.join(' ')

const nomeAluno = deslugify(route.params.aluno)

// Mapeamento de projetos por aluno (slug)
const projetosPorAluno = {
	'pedro-tomas-ribeiro-moura': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147600234/' },
	],
	'jose-pedro-pereira-santos': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147603884/' },
	],
	'diana-oliveira-mota': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147607415/' },
	],
	'franco-emmanuel-lagman': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147598472/' },
	],
	'afonso-goncalves-afonso': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147602123/' },
	],
	'lisa-silva-krol': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147599174/' },
	],
	'eduardo-goncalves-correia': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147599302/' },
	],
	'avan': [
		{ titulo: 'Projeto no Scratch', link: 'https://scratch.mit.edu/projects/1147599972/' },
	],
	'professor': [
		{ titulo: 'Projeto do Professor', link: 'https://scratch.mit.edu/projects/1146906303/' },
	],

}

const projetos = projetosPorAluno[route.params.aluno] || []
</script>
