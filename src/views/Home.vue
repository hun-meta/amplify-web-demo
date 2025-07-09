<template>
  <div class="home">
    <div class="hero-section">
      <h1>Vue.js 예제 앱에 오신 것을 환영합니다!</h1>
      <p>이 앱은 Vue.js의 기본 기능을 보여주는 간단한 예제입니다.</p>
      <button class="cta-button" @click="scrollToFeatures">더 알아보기</button>
    </div>
    
    <div class="features-section" ref="featuresSection">
      <h2>주요 기능</h2>
      <div class="features-grid">
        <div class="feature-card">
          <h3>반응형 디자인</h3>
          <p>모든 디바이스에서 완벽하게 작동하는 반응형 웹 페이지입니다.</p>
        </div>
        <div class="feature-card">
          <h3>라우팅</h3>
          <p>Vue Router를 사용하여 여러 페이지 간 부드러운 이동을 제공합니다.</p>
        </div>
        <div class="feature-card">
          <h3>컴포넌트 기반</h3>
          <p>재사용 가능한 Vue 컴포넌트로 구성된 모듈식 구조입니다.</p>
        </div>
      </div>
    </div>
    
    <div class="stats-section">
      <h2>실시간 통계</h2>
      <div class="stats-grid">
        <div class="stat-item">
          <h3>{{ visitCount }}</h3>
          <p>방문자 수</p>
        </div>
        <div class="stat-item">
          <h3>{{ currentTime }}</h3>
          <p>현재 시간</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      visitCount: 0,
      currentTime: ''
    }
  },
  mounted() {
    this.visitCount = Math.floor(Math.random() * 1000) + 100
    this.updateTime()
    setInterval(this.updateTime, 1000)
  },
  methods: {
    scrollToFeatures() {
      this.$refs.featuresSection.scrollIntoView({ behavior: 'smooth' })
    },
    updateTime() {
      this.currentTime = new Date().toLocaleTimeString('ko-KR')
    }
  }
}
</script>

<style scoped>
.home {
  min-height: 100vh;
}

.hero-section {
  text-align: center;
  padding: 4rem 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  margin-bottom: 3rem;
}

.hero-section h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.hero-section p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.cta-button {
  background-color: #fff;
  color: #667eea;
  border: none;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  border-radius: 25px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.cta-button:hover {
  transform: translateY(-2px);
}

.features-section {
  padding: 3rem 2rem;
  text-align: center;
}

.features-section h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: #2c3e50;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.feature-card {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-5px);
}

.feature-card h3 {
  color: #667eea;
  margin-bottom: 1rem;
}

.stats-section {
  padding: 3rem 2rem;
  background-color: #f8f9fa;
  text-align: center;
}

.stats-section h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: #2c3e50;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.stat-item {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.stat-item h3 {
  font-size: 2rem;
  color: #667eea;
  margin-bottom: 0.5rem;
}

.stat-item p {
  color: #6c757d;
  font-size: 1.1rem;
}
</style>