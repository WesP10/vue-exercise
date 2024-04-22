<template>
    <div id="body">
    <h1>About Me</h1>
    <p>Hello! I’m Weston Clark, a passionate web developer and aspiring software engineer. 🚀</p>

    <h2>My Journey:</h2>
    <p>Ever since I wrote my first line of HTML, I’ve been captivated by the magic of turning code into functional, beautiful websites. My journey has taken me through the realms of front-end development, where I’ve honed my skills in Vue.js, CSS, and responsive design.</p>

    <h2>This Project:</h2>
    <p>I built this website with Vue js to pratcice my frontend skills for my upcoming internship with Luraph. As far as I am aware Luraph uses Vue 3/Vite for their website, so I found 8 images and decided to build 8 interactive displays with the images.</p>

    <h2>Why Luraph?</h2>
    <p>Luraph is an cybersercurity company whose flagship product is a Lua script Obscufactor. Luraph’s commitment to innovation and cutting-edge solutions aligns perfectly with my own aspirations. As an intern here, I’m excited to contribute my creativity and technical expertise to real-world projects.</p>

    <h2>What I Bring:</h2>
    <ul>
        <li><b>Vue.js Mastery:</b> I’ve dived deep into Vue.js, crafting dynamic user interfaces and building seamless interactions.</li>
        <li><b>Responsive Design:</b> Ensuring that every pixel looks great across devices is my mantra.</li>
        <li><b>Collaboration:</b> I thrive in collaborative environments, eager to learn from experienced developers and contribute fresh ideas.</li>
    </ul>

    <h2>Let’s Connect:</h2>
    <p>I’m always up for a coding challenge or a chat about the latest tech trends. Feel free to reach out—I’d love to connect!</p>
    <ul>
      <li><a href="Westonclark393@gmail.com"><img width="60" height="60" src="https://img.icons8.com/papercut/60/new-post.png" alt="new-post"/> Email</a></li>
      <li><a href="https://www.linkedin.com/in/weston-clark-135ba4277/"><img width="48" height="48" src="https://img.icons8.com/fluency/48/linkedin.png" alt="linkedin"/> linkedin</a></li>
    </ul>
</div>
</template>

<script>
export default {
  name: 'AboutView'
}
</script>

<style scoped>
#body {
  display: block;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 14dvh;
  color: rgb(254, 254, 254);
}
h1, h2 {
  font-size: 2em;
  margin: 20px;
}
p {
  font-size: 1.5em;
  margin: 20px;
}
a {
  color: rgb(254, 254, 254);
  text-decoration: none;
  font-size: 2em;
  margin: 15px;
}
li {
  font-size: 1.5em;
  margin: 20px;
  list-style-type: none;
}
img {
  transform: translateY(.2em);
}
</style>
