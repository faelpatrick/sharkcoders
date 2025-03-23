<template>
	<v-app>
		<v-main class="bg-black text-white">
			<v-container>
				<div class="d-flex justify-center align-centerr">

					<h1 class="text-h5 mb-4 w-100" style="color: #8f88ba;">
						Projetos de {{ nomeAluno }}
					</h1>
					<v-divider class="mb-4" color="#fff1" />
					<v-btn class="mb-4" color="#8f88ba" variant="outlined" prepend-icon="mdi-arrow-left" @click="$router.back()">
						Voltar
					</v-btn>
				</div>

				<v-row v-if="projetos.length" class="d-flex justify-center">
					<v-col
v-for="(projeto, index) in projetos" :key="index" cols="12" md="6"
						class="d-flex flex-column align-center">
						<v-card :href="projeto.link" target="_blank" color="#8f88ba" dark>
							<!-- icone do scratch -->
					
							<v-card-title>
								{{ projeto.titulo }}
								<v-icon >mdi-arrow-right</v-icon> 
							</v-card-title>
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
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147600234' },
	],
	'jose-pedro-pereira-santos': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147603884' },
	],
	'diana-oliveira-mota': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147607415' },
	],
	'franco-emmanuel-lagman': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147598472' },
	],
	'afonso-goncalves-afonso': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147602123' },
	],
	'lisa-silva-krol': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147599174' },
	],
	'eduardo-goncalves-correia': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147599302' },
	],
	'edgar-habibi': [
		{ titulo: 'Jogo dos Presentes no Scratch', link: 'https://scratch.mit.edu/projects/1147599972' },
	],
	'professor': [
		{ titulo: 'Projeto do Professor', link: 'https://scratch.mit.edu/projects/1146906303' },
	],

}

const projetos = projetosPorAluno[route.params.aluno] || []
</script>
