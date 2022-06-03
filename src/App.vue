<template>
  <div id="app">
   <header>
     <h1>My Music</h1>
   </header>
   <main>
     <section class="player">
       <h2 class="song-title">{{current.title}} <span>{{ current.artist }}</span></h2>
       <div class="controls">
         <button class="prev" @click="prev">Prev</button>
         <button class="play" v-if="!isPlaying" @click="play">Play</button>
         <button class="pause" v-else @click="pause">Pause</button>
         <button class="next" @click="next">Next</button>
       </div>
     </section>
     <section class="playlist">
       <h3>The Playlist</h3>
       <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song'">
       {{ song.title }}
       </button>
     </section>
   </main>
  </div>
</template>

<script>


export default {
  name: 'App',
  data () {

    // STATE AND ARRAYS
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: 'Grateful',
          artist: 'Neffex',
          //src: require('./assets/neffe.mp3')
        },
        {
        title: 'Invincible',
        artist: 'Deaf Kev',
        //src: require('./assets/deaf-kev.mp3')
        }
      ],
      //player: new Audio()
    }
  },

  // METHODS
  methods: {

    play (song) {
      if (typeof song.src == "undefined") {
        this.current = song;
        //this.player.src = this.current.src;
      }

      //this.player.play();
      //this.player.addEventListener('ended', function () {
      //this.index++;

      // if (this.index > this.songs.length - 1) {
     //   this.index = 0;
     // }

    //  this.current = this.songs[this.index];
     // this.play(this.current);
      //}.bind(this));
      //this.isPlaying = true;
    },

    pause () {
      this.player.pause();
      this.isPlaying = false;
    }

    },

    next () {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }

      this.current = this.songs[this.index];
      this.play(this.current);
    },

    prev () {
      this.index--;
      if (this.index > 0) {
        this.index = 0;
        this.index = this.songs.length - 1;
      }

      this.current = this.songs[this.index];
      this.play(this.current);

    },

   created () {
    this.current = this.songs[this.index];
    //this.player.src = this.current.src;
    }
  }

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Courier New', Courier, monospace;
  background-color: rgb(7, 12, 10);
  color: antiquewhite;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color:black;
  color: aliceblue;
}

main {
  width: 100%;
  max-width: 768px;
  margin: 0 auto;
  padding: 30px;
}

.song-title {
  color: whitesmoke;
  font-size: 30px;
  font-weight: 500;
  text-transform: uppercase;
  text-align: center;
}

.song-title span {
  font-weight: 300;
}

.controls {
  justify-content: center;
  padding: 30px 15px;
  display: flex;
  align-items: center;
}

button {
  appearance: none;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
  color: aliceblue;
}

button:hover{
  background-color:rgb(69, 235, 179);
  color: rgb(43, 43, 43);
}

.play, .pause {
  font-size: 20px;
  font-weight: 700;
  padding: 15px 25px;
  margin: 0px 15px;
  border-radius: 8px;
  color: aliceblue;
  background-color: rgb(15, 15, 15);
}

.next, .prev {
  font-size: 16px;
  font-weight: 700;
  padding: 10px 20px;
  margin: 0px 15px;
  border-radius: 6px;
  color: aliceblue;
  background-color: rgb(44, 44, 44);
}

.playlist {
  padding: 0px 30px;
}

.playlist h3 {
  color: antiquewhite;
  font-size: 29px;
  font-weight: 400;
  margin-bottom: 30px;
  text-align: center;
}

.playlist .song {
  display: block;
  width: 100%;
  padding: 15px;
  font-size: 20px;
  font-weight: 700;
  cursor: pointer;
}

.playlist .song:hover{
  color: aquamarine;
}

.playlist .song.playing {
  color: whitesmoke;
  background-image: linear-gradient(to right,  rgb(44, 44, 44), rgb(69, 235, 179) );
}

.playlist .song:hover {
  color: black;
}
</style>
