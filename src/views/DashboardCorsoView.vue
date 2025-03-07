<template>
  <div class="container mx-auto p-4">
    <h1 style="color: black; font-size: 2.5rem; text-align: center; font-weight: bold;">Ecco a te i corsi</h1>



    <button @click="$router.push('/gestione-corso')" class="bg-blue-500 text-white px-4 py-2 rounded mb-4">
      + Aggiungi Corso
    </button>

    <div v-if="corsi.length > 0">
      <CorsoCard v-for="corso in corsi" :key="corso.id" :corso="corso" @modifica="modificaCorso" @elimina="eliminaCorso" />
    </div>
    <p v-else class="text-gray-500">Nessun corso disponibile.</p>
  </div>
</template>

<script>
import CorsoCard from "@/components/CorsoCard.vue";

export default {
  components: { CorsoCard },
  data() {
    return {
      corsi: [] // Da caricare via API
    };
  },
  methods: {
    modificaCorso(id) {
      this.$router.push(`/gestione-corso/${id}`);
    },
    eliminaCorso(id) {
      this.corsi = this.corsi.filter(corso => corso.id !== id);
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 800px;
}

h1 {
  font-size: 2.5rem;  /* Aumenta la dimensione */
  font-weight: bold;  /* Mantiene il grassetto */
  color: black;  /* Cambia colore in blu */
  text-align: center;  /* Centra il testo */
}
</style>

