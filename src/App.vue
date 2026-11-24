<script setup>
  import {ref} from 'vue'

  const abaAtiva = ref('transferencias')

  const abas = [
    { id: 'transferencias', nome: 'Transferências' },
    { id: 'consultas', nome: 'Consultas' },
    { id: 'massa', nome: 'Consulta em massa' }
  ]

  import transferencias from './components/transferencias.vue'
</script>

<template>
  <header>
    <div class="titulo">
      <h1>Transf-Bot</h1>
    </div>
  </header>

  <main>
    <div class="tela-inteira">
      <div class="retangulo">
        <div class="abas">
          <button
            v-for="aba in abas"
            :key="aba.id"
            :class="{ ativa: abaAtiva === aba.id }"
            @click="abaAtiva = aba.id"
          >
            {{ aba.nome }}
          </button>
        </div>
      
        <div class="conteudo">
          <div v-if="abaAtiva === 'transferencias'">
            <transferencias />
          </div>

          <div v-else-if="abaAtiva === 'consultas'">
            <h3>Configurações</h3>
            <p>Ajustes do sistema aqui.</p>
          </div>

          <div v-else-if="abaAtiva === 'massa'">
            <h3>Sobre</h3>
            <p>Detalhes da aplicação.</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.tela-inteira {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f4f4f9;
}

/* O retângulo central */
.retangulo {
  width: 500px;
  min-height: 300px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

/* Estilo das abas */
.abas {
  display: flex;
  border-bottom: 1px solid #ddd;
  background-color: #fafafa;
}

.abas button {
  flex: 1;
  padding: 12px;
  border: none;
  background: none;
  cursor: pointer;
  font-weight: 500;
  color: #666;
  transition: 0.2s;
}

.titulo {
  display: flex;
  justify-content: center;
}

.abas button:hover {
  background-color: #f0f0f0;
}

.abas button.ativa {
  color: #42b883; /* Verde clássico do Vue */
  border-bottom: 2px solid #42b883;
  background-color: white;
}

.conteudo {
  padding: 20px;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}


</style>
