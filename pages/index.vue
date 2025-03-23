<template>
	<v-app>
		<v-main class="bg-black text-white">
			<v-container class="text-center py-10">
				<v-img src="/sharkcoders-logo.png" max-width="200" class="mx-auto mb-6" />
				<v-img src="/faelpatrick.png" max-width="150" class="mx-auto mb-10 rounded-circle " />

				<h1 class="text-h5 mb-6" style="color: #8f88ba;">Turmas do Prof. Rafael</h1>

				<v-row justify="center" dense>
					<v-col v-for="turma in turmas" :key="turma.nome" cols="12" sm="6" md="3">
						<v-card :to="`/turmas/${turma.slug}`" link class="text-white" :style="`background-color: #8f88ba`">
							<v-card-title>{{ turma.nome }}</v-card-title>
						</v-card>
					</v-col>
				</v-row>
			</v-container>
		</v-main>
	</v-app>
</template>

<script setup>
const turmas = [
	{ nome: 'CODE KIDS LOGIC & CODING (Sábado 10h às 11:30h)', slug: 'code-kids' },
	{ nome: 'PRE-CODE EXPLORE & CREATE (Sábado 11:30h às 12:45h)', slug: 'pre-code' },
	{ nome: 'CODE TEENS | WEB DEVELOPMENT (Sábado 14h às 15:30h)', slug: 'code-teens' },
	{ nome: 'PYTHON PROGRAMMER FOR AI (Sábado 15:30h)', slug: 'python-ai' },
]
</script>
