<script setup>
import { onMounted } from 'vue';
import { useMembresStore } from '@/stores/membres'
import { useRoute } from 'vue-router'
import { reactive } from 'vue';

const state = reactive({
    membre: null
});

const route = useRoute();

const membresStore = useMembresStore();

onMounted(() => {
  state.membre = membresStore.getMembre(route.params.id)
  
})

</script>

<template>

<div class="card">
  <div class="card-content">
    <p class="title">
     {{state.membre.fullname}}
    </p>
    <p class="subtitle">
    oui
    </p>
  </div>
  <footer class="card-footer">
    <p class="card-footer-item">
      oui
    </p>
    <p class="card-footer-item">
      <span>
       Compte créé le <time>{{ state.membre.created_at}}</time>
      </span>
    </p>
  </footer>
</div>

</template>
