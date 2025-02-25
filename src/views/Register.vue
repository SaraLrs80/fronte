<template>
  <div class="register-container">
    <h2>Créer un compte</h2>
    <form @submit.prevent="register">
      <input v-model="nom" type="text" placeholder="Nom" required />
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="motDePasse" type="password" placeholder="Mot de passe" required />
      <input v-model="confirmPassword" type="password" placeholder="Confirmer le mot de passe" required />
      <button type="submit">S'inscrire</button>
      <p class="login-link">
        Déjà inscrit ? <router-link to="/login">Se connecter</router-link>
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
      nom: "",
      email: "",
      motDePasse: "",
      confirmPassword: "",
      errorMessage: null,
    };
  },
  methods: {
    ...mapActions("auth", ["register"]), // Connecte la méthode register() à l'action Vuex
    async register() {
      if (this.motDePasse !== this.confirmPassword) {
        this.errorMessage = "Les mots de passe ne correspondent pas ❌";
        return;
      }

      try {
        await this.register({ nom: this.nom, email: this.email, motDePasse: this.motDePasse });
        this.$router.push("/login"); // Redirection après inscription
      } catch (error) {
        this.errorMessage = error?.message || "Erreur d'inscription ❌";
      }
    },
  },
};
</script>
