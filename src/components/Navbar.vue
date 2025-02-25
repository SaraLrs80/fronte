<template>
    <header class="header">
      <nav>
        <router-link to="/" exact-active-class="active">Home</router-link>
        <router-link to="/library" exact-active-class="active">Bookshelf</router-link>
        <router-link to="/circulation" exact-active-class="active">Book Circulation</router-link>
        <router-link to="/about" exact-active-class="active">About</router-link>
        <router-link to="/contact" exact-active-class="active">Contact Us</router-link>
        <div class="auth-links">
          <router-link to="/register" exact-active-class="active">Sign Up</router-link>
          <router-link to="/login" exact-active-class="active">Sign In</router-link>
        </div>
      </nav>
    </header>
  </template>
  
  <style scoped>
  .header {
    width: 100%;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #f8f8f8; /* Modifier selon Figma */
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  
  nav {
    display: flex;
    gap: 30px;
  }
  
  .auth-links {
    margin-left: auto;
  }
  
  nav a {
    color: #333; /* Couleur texte selon Figma */
    font-size: 18px;
    font-weight: bold;
    text-decoration: none;
    padding: 10px 15px;
    transition: 0.3s;
  }
  
  nav a:hover {
    color: white;
    background-color: black;
    border-radius: 8px;
  }
  
  .active {
    color: white;
    background-color: black;
    border-radius: 8px;
  }
  </style>
  