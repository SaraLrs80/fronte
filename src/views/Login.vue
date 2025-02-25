<template>
  <div class="login-container">
    <h2>Connexion</h2>
    <form @submit.prevent="login">
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="motDePasse" type="password" placeholder="Mot de passe" required />
      <button type="submit">Se connecter</button>
      <p class="register-link">
        Pas encore inscrit ? <router-link to="/register">Créer un compte</router-link>
      </p>
      <p class="forgot-password">
        <router-link to="/reset-password">Mot de passe oublié ?</router-link>
      </p>
    </form>
    <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
  </div>
</template>

<script>
import { mapActions } from "vuex"; // Import Vuex pour appeler l'action

export default {
  data() {
    return {
      email: "",
      motDePasse: "",
      errorMessage: null,
    };
  },
  methods: {
    ...mapActions("auth", ["login"]), // Connecte la méthode login() à l'action Vuex
    async login() {
      try {
        await this.login({ email: this.email, motDePasse: this.motDePasse });
        this.$router.push("/"); // Redirection après connexion
      } catch (error) {
        this.errorMessage = error?.message || "Erreur de connexion ❌";
      }
    },
  },
};
</script>
