<template>
    <div class="game-match-wrapper">
      <div class="container py-5">
        <h1 class="text-center text-white mb-5">Game Match</h1>
        
        <div class="row">
          <div class="col-md-4 mb-4">
            <div class="user-profile p-4">
              <img src="" alt="Your Profile" class="rounded-circle mb-3">
              <h2 class="text-white">Your Profile</h2>
              <p class="text-white-50">Your Games:</p>
              <div class="game-list">
                <span v-for="game in yourGames" :key="game" class="game-tag">{{ game }}</span>
              </div>
            </div>
          </div>
          
          <div class="col-md-4 mb-4">
            <div class="match-area p-4">
              <h3 class="text-white text-center mb-4">Potential Match</h3>
              <div class="match-percentage">
                <svg viewBox="0 0 36 36" class="circular-chart">
                  <path class="circle-bg" d="M18 2.0845
                    a 15.9155 15.9155 0 0 1 0 31.831
                    a 15.9155 15.9155 0 0 1 0 -31.831" />
                  <path class="circle" :stroke-dasharray="`${matchPercentage}, 100`" d="M18 2.0845
                    a 15.9155 15.9155 0 0 1 0 31.831
                    a 15.9155 15.9155 0 0 1 0 -31.831" />
                  <text x="18" y="20.35" class="percentage">{{ matchPercentage }}%</text>
                </svg>
              </div>
              <div class="text-center mt-4">
                <button @click="findMatch" class="btn btn-success btn-lg custom-button">Find Match</button>
              </div>
            </div>
          </div>
          
          <div class="col-md-4 mb-4">
            <div class="user-profile p-4">
              <img src="" alt="Potential Match Profile" class="rounded-circle mb-3">
              <h2 class="text-white">Potential Match</h2>
              <p class="text-white-50">Their Games:</p>
              <div class="game-list">
                <span v-for="game in matchGames" :key="game" class="game-tag" 
                      :class="{ 'matching-game': yourGames.includes(game) }">
                  {{ game }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const yourGames = ref(['Fortnite', 'Minecraft', 'Among Us', 'Rocket League', 'Fall Guys']);
  const matchGames = ref(['Minecraft', 'Among Us', 'Valorant', 'CS:GO', 'Apex Legends']);
  const matchPercentage = ref(60);
  
  const findMatch = () => {
    // Simulate finding a new match
    matchGames.value = ['Fortnite', 'Minecraft', 'Rocket League', 'Overwatch', 'League of Legends'];
    matchPercentage.value = Math.floor(Math.random() * (100 - 40 + 1) + 40); // Random between 40-100
  };
  </script>
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');
  
  .game-match-wrapper {
    background-image: url('/public/img/FONDO WEB.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    min-height: 100vh;
    font-family: 'Poppins', sans-serif;
    padding: 2rem 0;
  }
  
  .user-profile, .match-area {
    background-color: rgba(0, 0, 0, 0.6);
    border-radius: 15px;
    backdrop-filter: blur(10px);
  }
  
  .game-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }
  
  .game-tag {
    background-color: rgba(255, 255, 255, 0.1);
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 15px;
    font-size: 0.9rem;
  }
  
  .matching-game {
    background-color: rgba(40, 167, 69, 0.6);
  }
  
  .circular-chart {
    display: block;
    margin: 0 auto;
    max-width: 150px;
  }
  
  .circle-bg {
    fill: none;
    stroke: rgba(255, 255, 255, 0.1);
    stroke-width: 3.8;
  }
  
  .circle {
    fill: none;
    stroke: #28a745;
    stroke-width: 2.8;
    stroke-linecap: round;
    animation: progress 1s ease-out forwards;
  }
  
  @keyframes progress {
    0% {
      stroke-dasharray: 0 100;
    }
  }
  
  .percentage {
    fill: #fff;
    font-size: 0.5em;
    text-anchor: middle;
  }
  
  .custom-button {
    background: linear-gradient(45deg, #28a745, #34d058);
    border: none;
    padding: 0.8rem 2rem;
    font-weight: 600;
    transition: all 0.3s ease;
  }
  
  .custom-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(40, 167, 69, 0.4);
  }
  
  @media (max-width: 768px) {
    .game-match-wrapper {
      padding: 1rem 0;
    }
    
    .user-profile, .match-area {
      margin-bottom: 2rem;
    }
  }
  </style>
  
  