<template>
  <v-app>
    <v-main class="bg-black text-white">
      <v-container>
        <div class="d-flex justify-center align-centerr">

          <h1 class="text-h5 mb-6" style="color: #8f88ba;">
            {{ nomeTurma || 'Turma não encontrada' }}
          </h1>
          <v-spacer />
          <v-btn class="mb-4" color="#8f88ba" variant="outlined" prepend-icon="mdi-arrow-left" @click="$router.back()">
            Voltar
          </v-btn>
        </div>


        <v-list lines="one">
          <v-list-item v-for="aluno in alunos" :key="aluno" :title="aluno" :to="`/alunos/${slugify(aluno)}`" />

        </v-list>
      </v-container>
    </v-main>
  </v-app>
</template>


<script setup>
const route = useRoute()

// Simulação: nomes fictícios por turma
const turmas = {
  'code-kids': {
    nome: 'CODE KIDS LOGIC & CODING',
    alunos: [
      'Afonso Gonçalves Afonso',
      'Diana Oliveira Mota',
      'Edgar Habibi',
      'Eduardo Gonçalves Correia',
      'Franco Emmanuel Lagman',
      'José Pedro Pereira Santos',
      'Lisa Silva Krol',
      'Pedro Tomás Ribeiro Moura',
    ]

  },
  'pre-code': {
    nome: 'PRE-CODE EXPLORE & CREATE',
    alunos: ['Daniela', 'Eduardo', 'Fernanda']
  },
  'code-teens': {
    nome: 'CODE TEENS | WEB DEVELOPMENT',
    alunos: ['Gabriel', 'Helena', 'Igor']
  },
  'python-ai': {
    nome: 'PYTHON PROGRAMMER FOR AI',
    alunos: ['João', 'Karina', 'Lucas']
  }
}

const turma = turmas[route.params.turma]
const nomeTurma = turma?.nome || ''
const alunos = turma?.alunos || []

const slugify = (nome) => nome.toLowerCase()
  .normalize('NFD').replace(/[\u0300-\u036f]/g, '') // remove acentos
  .replace(/[^a-z0-9]/g, '-')                       // espaços e símbolos -> hífen
  .replace(/-+/g, '-')                              // múltiplos hífens viram um
  .replace(/^-|-$/g, '')                            // remove hífens extremos
</script>
