<template>
  <div class="about">
    <div class="about-header">
      <h1>소개</h1>
      <p>이 프로젝트에 대해 자세히 알아보세요</p>
    </div>
    
    <div class="about-content">
      <div class="content-section">
        <h2>프로젝트 개요</h2>
        <p>이 Vue.js 예제 앱은 현대적인 웹 개발의 기본 원칙을 보여주는 간단한 데모 애플리케이션입니다. 
        Vue.js의 핵심 기능들을 활용하여 반응형 사용자 인터페이스를 구현했습니다.</p>
      </div>
      
      <div class="content-section">
        <h2>사용된 기술</h2>
        <div class="tech-grid">
          <div class="tech-item">
            <h3>Vue.js 3</h3>
            <p>최신 Vue.js 프레임워크를 사용하여 컴포넌트 기반 UI를 구현했습니다.</p>
          </div>
          <div class="tech-item">
            <h3>Vue Router</h3>
            <p>SPA (Single Page Application) 라우팅을 위한 공식 라우터를 사용했습니다.</p>
          </div>
          <div class="tech-item">
            <h3>CSS3</h3>
            <p>모던 CSS 기술을 활용하여 아름다운 UI를 구현했습니다.</p>
          </div>
          <div class="tech-item">
            <h3>JavaScript ES6+</h3>
            <p>최신 JavaScript 문법을 사용하여 깔끔한 코드를 작성했습니다.</p>
          </div>
        </div>
      </div>
      
      <div class="content-section">
        <h2>주요 특징</h2>
        <div class="features-list">
          <div class="feature-item">
            <div class="feature-icon">📱</div>
            <div class="feature-text">
              <h3>반응형 디자인</h3>
              <p>모든 디바이스에서 완벽하게 작동하는 반응형 레이아웃</p>
            </div>
          </div>
          <div class="feature-item">
            <div class="feature-icon">🚀</div>
            <div class="feature-text">
              <h3>빠른 성능</h3>
              <p>Vue.js의 가상 DOM을 활용한 효율적인 렌더링</p>
            </div>
          </div>
          <div class="feature-item">
            <div class="feature-icon">🎨</div>
            <div class="feature-text">
              <h3>모던 UI</h3>
              <p>깔끔하고 직관적인 사용자 인터페이스</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="content-section">
        <h2>개발 정보</h2>
        <div class="info-grid">
          <div class="info-item">
            <strong>개발 기간:</strong> {{ developmentTime }}
          </div>
          <div class="info-item">
            <strong>마지막 업데이트:</strong> {{ lastUpdate }}
          </div>
          <div class="info-item">
            <strong>버전:</strong> {{ version }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      developmentTime: '2024년 1월',
      lastUpdate: new Date().toLocaleDateString('ko-KR'),
      version: '1.0.0'
    }
  }
}
</script>

<style scoped>
.about {
  min-height: 100vh;
  padding: 2rem 0;
}

.about-header {
  text-align: center;
  padding: 2rem;
  background: linear-gradient(135deg, #74b9ff 0%, #0984e3 100%);
  color: white;
  margin-bottom: 3rem;
}

.about-header h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.about-header p {
  font-size: 1.2rem;
  opacity: 0.9;
}

.about-content {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 2rem;
}

.content-section {
  margin-bottom: 3rem;
}

.content-section h2 {
  font-size: 1.8rem;
  color: #2c3e50;
  margin-bottom: 1.5rem;
  border-bottom: 3px solid #74b9ff;
  padding-bottom: 0.5rem;
}

.content-section p {
  line-height: 1.8;
  color: #555;
  font-size: 1.1rem;
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.tech-item {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  border-left: 4px solid #74b9ff;
}

.tech-item h3 {
  color: #74b9ff;
  margin-bottom: 0.5rem;
}

.features-list {
  margin-top: 2rem;
}

.feature-item {
  display: flex;
  align-items: flex-start;
  margin-bottom: 2rem;
  padding: 1.5rem;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.feature-icon {
  font-size: 2rem;
  margin-right: 1.5rem;
  background: #74b9ff;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.feature-text h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.feature-text p {
  color: #666;
  margin: 0;
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.info-item {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 8px;
  border-left: 4px solid #74b9ff;
}

.info-item strong {
  color: #2c3e50;
  display: block;
  margin-bottom: 0.5rem;
}
</style>