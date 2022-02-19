<template>
  <div>
    <header>
      <h1>My Anime Feed</h1>
    </header>
    <main>
      <AnimePost v-for="(anime, i) in anime_list" :key="i" :anime="anime"/>
    </main>
  </div>
</template>

<script>
import AnimePost from "./components/AnimePost.vue";

export default {
  name: 'App',
  data () {
    return {
      anime_list: []
    }
  },
  components: {
    AnimePost,
  },
  methods: {
    getAnime() {
      const anime_titles = [
        "Naruto",
        "Demon Slayer",
        "Dragon Ball",
        "My Hero Academia",
        "Sword Art Online",
        "Tokyo Ghoul",
        "Code Geass",
        "One Piece",
        "Fairy Tail",
        "Attack On Titan",
        "Hunter x Hunter",
      ];

      const anime = [];

      for (let i = 0; i < 10; i++) {
        anime.push({
          title: anime_titles[
            Math.floor(Math.random() * anime_titles.length)
          ],
          description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec viverra massa bibendum malesuada luctus. Nulla bibendum velit a rutrum sodales. Nulla accumsan nulla nec venenatis suscipit. Phasellus vestibulum, tortor sit amet placerat mattis, purus velit accumsan sapien, nec eleifend libero nisi vel nisi. Duis rhoncus ex et justo ultricies,"
        });
      }

      return anime;
    },
    handleScroll () {
      if (window.scrollY + window.innerHeight > document.body.scrollHeight - 50) {
        this.anime_list = [
          ...this.anime_list, ...this.getAnime()
        ]
      }
    }
  },
  mounted () {
    this.anime_list = this.getAnime()
    window.addEventListener('scroll', this.handleScroll);
  }
};
</script>

<style>
* {
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  background-color: #2c3e50;
  min-height: 100vh;
  padding-top: 3rem;
}

header h1 {
  text-align: center;
}

header {
  margin-bottom: 2rem;
}

main {
  padding: 0 2rem;
  max-width: 640px;
  margin: 0 auto;
}
</style>
