<template>
  <div class="main">
    <div class="wright-box">
     <h1>{{title}}</h1>
     <form @submit.prevent="addPost">
       <input v-model="newPostTitle" placeholder="Post Title"/><br>
       <textarea v-model="newPostBody" placeholder="Post Body"></textarea><br>
       <button type="submit">Add Post</button>
     </form>
    </div>
    
    <div class="blog-box">
      <h1>Blog box</h1>
      <div class="row">
        <div v-for="post in posts" :key="post.id">
          <h3>{{post.title}}</h3>
          <p>{{post.body}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "My Blog",
      posts: [
        { id: 1, title: "First Post", body: "This is my first post" },
        { id: 2, title: "Second Post", body: "This is my second post" }
      ],
      newPostTitle: "",
      newPostBody: "",
      nextPostId: 3
    };
  },
  methods: {
    addPost() {
      this.posts.push({
        id: this.nextPostId++,
        title: this.newPostTitle,
        body: this.newPostBody
      });
      this.newPostTitle = "";
      this.newPostBody = "";
    }
  }
};
</script>

<style>
body{
  padding: 20px;
}
.main{
  display: flex;
  justify-content: space-around;
}
.wright-box{
  border: 1px solid gray;
  padding: 30px;
  border-radius: 20px;
  width: 40%;
}
input,textarea{
  width: 90%;
  margin-top: 20px;
  padding-left: 15px;
  border: 1px solid gainsboro;
  border-radius: 4px;
  outline: none;
}
input{
  height: 30px;
}
textarea{
  height: 150px;
}
button{
  width: 93%;
  padding: 10px;
  font-size: 20px;
  margin-top: 20px;
  background-image: linear-gradient(to right, #767af2, rgb(107, 14, 79));
  color: aliceblue;
  border: 1px solid gainsboro;
  border-radius: 4px;
}

.blog-box{
  width: 50%;
  border: 1px solid gray;
  border-radius: 20px;
  display: block;
  padding: 20px;
}
.row div{
  background-color: rgb(217, 230, 248);
  text-align: left;
  border-radius: 0 4px 4px 0;
}
.row div h3{
  border-radius: 4px 0 0 4px;
  border-left: 10px solid #767af2;
  width: 30%;
  padding: 10px 0px 10px 20px;
  margin-top: 5px;
}
.row div p{
  margin-bottom: 5px;
  padding-bottom: 10px;
  padding-left: 200px;
  margin-top: -47px;
  width: 60%;
}
.row div:hover{
  box-shadow: 1px 1px 8px #333340;
}
</style>