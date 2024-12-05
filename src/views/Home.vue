<template>
  <div class="home">
    <!-- 顶部栏 -->
    <div class="top-bar">
      <div class="search-bar">
        <div class="search-input">
          <svg viewBox="0 0 24 24" class="search-icon">
            <path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
          </svg>
          <input 
            type="text" 
            placeholder="Search songs, albums, artists, podcasts"
            v-model="searchQuery"
          >
        </div>
      </div>
      <div class="welcome-text">
        Welcome bai
      </div>
    </div>

    <!-- 快捷标签 -->
    <div class="mood-tags">
      <button v-for="tag in moodTags" :key="tag" class="tag">
        {{ tag }}
      </button>
    </div>

    <!-- 推荐音乐区域 -->
    <section class="music-section">
      <div class="section-header">
        <h2>MUSIC TO GET YOU STARTED</h2>
        <div class="controls">
          <button class="play-all">Play all</button>
          <div class="nav-buttons">
            <button class="nav-btn prev">
              <svg viewBox="0 0 24 24"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z"/></svg>
            </button>
            <button class="nav-btn next">
              <svg viewBox="0 0 24 24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z"/></svg>
            </button>
          </div>
        </div>
      </div>
      
      <div class="music-grid">
        <div v-for="song in songs" :key="song.id" class="song-card">
          <div class="cover-wrapper">
            <img :src="song.cover" :alt="song.title">
            <button class="play-button">
              <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>
            </button>
          </div>
          <div class="song-info">
            <h3>{{ song.title }}</h3>
            <p>{{ song.artist }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const searchQuery = ref('')

const moodTags = [
  'Podcasts', 'Energize', 'Workout', 'Feel good', 
  'Party', 'Relax', 'Commute', 'Romance', 'Sad', 
  'Focus', 'Sleep'
]

const songs = ref([
  {
    id: 1,
    title: 'Hotel California',
    artist: 'Eagles • 700M plays • Legacy',
    cover: 'https://i.ytimg.com/vi/EqPtz5qN7HM/maxresdefault.jpg'
  },
  {
    id: 2,
    title: 'Tennessee Whiskey',
    artist: 'Chris Stapleton • 1.2M • Traveller',
    cover: 'https://i.ytimg.com/vi/4zAThXFOy2c/maxresdefault.jpg'
  },
  {
    id: 3,
    title: 'All I Want for Christmas Is You',
    artist: 'Mariah Carey • Merry Christmas',
    cover: 'https://i.ytimg.com/vi/aAkMkVFwAoo/maxresdefault.jpg'
  },
  {
    id: 4,
    title: 'Please Please Please',
    artist: 'Sabrina Carpenter • Short n Sweet',
    cover: 'https://i.ytimg.com/vi/P-WP6POdTgY/maxresdefault.jpg'
  }
])
</script>

<style scoped>
.home {
  color: white;
  padding: 20px 40px;
}

.top-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
}

.welcome-text {
  font-size: 14px;
  color: #fff;
  padding: 6px 12px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  margin-left: 20px;
}

.search-bar {
  flex: 1;
  max-width: 600px;
}

.search-icon {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
  fill: #aaa;
}

.search-input input {
  width: 100%;
  padding: 12px 20px 12px 44px;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  color: white;
  font-size: 16px;
}

.search-input input::placeholder {
  color: #aaa;
}

.mood-tags {
  display: flex;
  gap: 12px;
  margin: 32px 0;
  flex-wrap: wrap;
}

.tag {
  padding: 8px 16px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  color: white;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.2s;
}

.tag:hover {
  background: rgba(255, 255, 255, 0.2);
}

.section-header {
  margin-bottom: 24px;
}

.section-header h2 {
  color: #aaa;
  font-size: 14px;
  margin: 0 0 8px;
}

.section-header h1 {
  display: none;
}

.controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.play-all {
  background: #030303;
  color: white;
  border: none;
  padding: 8px 24px;
  border-radius: 20px;
  cursor: pointer;
  font-size: 14px;
}

.nav-buttons {
  display: flex;
  gap: 8px;
}

.nav-btn {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-btn svg {
  width: 20px;
  height: 20px;
  fill: white;
}

.music-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 24px;
  margin-top: 24px;
}

.song-card {
  position: relative;
}

.cover-wrapper {
  position: relative;
  margin-bottom: 12px;
}

.cover-wrapper img {
  width: 100%;
  aspect-ratio: 16/9;
  object-fit: cover;
  border-radius: 4px;
}

.play-button {
  position: absolute;
  right: 8px;
  bottom: 8px;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.7);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.2s;
}

.song-card:hover .play-button {
  opacity: 1;
}

.play-button svg {
  width: 24px;
  height: 24px;
  fill: white;
}

.song-info h3 {
  margin: 0;
  font-size: 14px;
  font-weight: 500;
}

.song-info p {
  margin: 4px 0 0;
  font-size: 12px;
  color: #aaa;
}
</style> 