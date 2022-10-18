<script>
export default {
  data() {
    return {
        pseudo:"",
        message:"",
    };
  },

  methods: {
    togglePost (){
        this.showCreatePost = !this.showCreatePost
      },
    async post() {
      const options = {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Authorization: "bearer token",
        },
        body: {
          title: String,
          content: String,
        },
      };

      const response = await fetch ("https://social-network-api.osc-fr1.scalingo.io/chat-match/post",
        options)

        const data = await response.json()
    },
  },
};
</script>

<template>
  <div id="card-post">
  <form>
    <h2>Racontes-nous quelque-chose ! </h2>
    <textarea name="" id="" cols="" rows=""></textarea>
    <input @submit="togglePost"  type="submit" name="" id="inputCreatePost" value="Poster">
  </form>
  </div>
</template>

<style scoped>
#card-post{
padding-top: 20px;
margin-top: 20px;
background-color: white;
display: flex;
flex-direction: column;
border-radius: 20px;
box-shadow: 1px 1px 5px 1px lightgray;
}
form{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

textarea{
  margin-top: 20px;
  cursor: pointer;
  width: 300px;
  height: 100px;
  resize: none;
  background-color: white;
  border: 1px solid grey;
  outline: none;
  padding: 5px;
  box-shadow: 0.5px 0.5px 2.5px 0.5px lightgray;
  border-radius: 5px;
  font-family: Inter, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  scroll-behavior: smooth;
}

#inputCreatePost{
  display: flex;
  text-align: center;
  align-items: center;
  margin: 20px;
  padding: 10px;
  background-color: #fe8c0e;
  color: white;
  border: 0px;
  border-radius: 5px;
  font-size: 15px;
}
#inputCreatePost:hover{
  cursor: pointer;
  background-color: #f9ddbe;
  color: #fe8c0e;
  transition: all 0.2s;
}
</style>
