<template>
  <div id="app">
    <div class="container">
      <header>
        <h1 style="font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;">TUGAS 4</h1>
      </header>

      <!-- Click Counter -->
      <section class="section">
        <h2>Click Counter</h2>
        <p class="counter-text">You clicked <span>{{ count }}</span> times</p>
        <button @click="count++" class="btn">Click Me</button>
      </section>

      <!-- Box Color Changer -->
      <section class="section">
        <h2>Color Changer</h2>
        <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
        <button @click="changeColor" class="btn">Change Color</button>
      </section>

      <!-- Image Carousel -->
      <section class="section">
        <h2>Image Carousel</h2>
        <div class="carousel">
          <button @click="prevImage" class="carousel-btn">❮</button>
          <img :src="images[currentImage]" alt="Carousel" class="carousel-image">
          <button @click="nextImage" class="carousel-btn">❯</button>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      boxColor: 'skyblue',
      images: [
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS9NHCiGebZcOMcOMUA-IFoyIvz-wfyClt5Lw&s',
        'https://cdn.oneesports.id/cdn-data/sites/2/2022/03/Naruto-Uzumaki.jpg',
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSECyWQWniPlt1vNhN1xe_fPAhCLX73j_7MZg&s',
      ],
      currentImage: 0,
    };
  },
  methods: {
    changeColor() {
      const colors = ['skyblue', 'lightcoral', 'lightgreen', 'plum', 'lightgoldenrodyellow'];
      this.boxColor = colors[Math.floor(Math.random() * colors.length)];
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
  },
};
</script>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 110vh;
  background-color: #5D9F9AFF;
  font-family: 'Arial', sans-serif;
}

.container {
  text-align: center;
  max-width: 800px;
  padding: 50px;
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

header h1 {
  font-size: 3em;
  margin-bottom: 20px;
  color: #333;
}

.section {
  margin-bottom: 20px;
}

.section h2 {
  font-size: 1.5em;
  margin-bottom: 10px;
  color: #555;
}

.counter-text {
  font-size: 1.2em;
  margin-bottom: 10px;
}

.counter-text span {
  font-weight: bold;
  color: #42b983;
}

.color-box {
  width: 100px;
  height: 100px;
  margin: 10px auto;
  border-radius: 8px;
  transition: background-color 0.3s ease;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.carousel-image {
  width: 150px;
  height: 100px;
  border-radius: 8px;
  object-fit: cover;
}

.carousel-btn {
  background-color: #42b983;
  color: white;
  border: none;
  font-size: 1.5em;
  padding: 8px;
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.carousel-btn:hover {
  background-color: #35495e;
}

.btn {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 1em;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #35495e;
}
</style>
