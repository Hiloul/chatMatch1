<template>
    <h1>Créer un compte</h1>
    <form action="">
        <input type="text" placeholder="Nom">
        <input type="text" placeholder="Prénom">
        <input type="email" placeholder="Mail">
        <input type="text" placeholder="Pseudo">
        <input type="text" placeholder="Mot de passe">
    </form>
</template>

<style scoped>
h1{text-align: center;
text-decoration: underline;
padding: 5px;
color: #FE8C0E;}
form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 20px;
}
input{
    padding: 10px;
    margin: 10px;
    border-radius: 10px;
}
</style>