<script>

</script>


<template>
    <div>
    <h1>Créer un compte</h1>
    
    <form action="">
       
<input  placeholder="Nom" id="nom">
        <input type="text" placeholder="Prénom">
    <input type="email" placeholder="Mail">
         <input type="text" placeholder="Pseudo">
        <input type="password" placeholder="Mot de passe">
    </form>
    <button>S'inscrire</button>
</div>
</template>

<style scoped>
div{
    background-color: white;
   height: 340px;
   padding: 5px;
   box-shadow: 2px 2px 10px 2px lightgray;
border-radius: 50px;
}
h1 {
    text-align: center;
    text-decoration: underline;
    padding: 5px;
    color: #FE8C0E;
    
}

form {
    display: flex;
    flex-direction: column;
    gap: 1rem;

    text-align: center;
}

input {
    margin-left: 25%;
    padding: 10px;
 text-align: justify;
    border-radius: 10px;
    margin-top: 0.25rem;
   
    padding: 6px;
    border-radius: 8px;
    border: 1px solid rgb(217, 216, 216);
    box-shadow: 1px 1px 5px 1px lightgray;
    outline: none;
    max-width: 50%;
    
}
button{  margin-left: 45%;
    padding: 10px;
 text-align: justify;
    border-radius: 10px;
    margin-top: 0.30rem;
    padding: 6px;
    border-radius: 8px;
    border:none;
    font-weight: 600;
    outline: none;
    background-color:#FE8C0E ;
    color: white;

}
button:hover{
    background-color: #FFEEDD;
    box-shadow: 1px 1px 5px 1px lightgray;
    color: #FE8C0E;
    transition: all 0.3s;
}

</style>