<template>
  <div class="contact">
    <div class="contact-header">
      <h1>연락처</h1>
      <p>궁금한 점이 있으시면 언제든지 연락주세요</p>
    </div>
    
    <div class="contact-content">
      <div class="contact-info">
        <h2>연락 정보</h2>
        <div class="info-cards">
          <div class="info-card">
            <div class="info-icon">📧</div>
            <div class="info-details">
              <h3>이메일</h3>
              <p>contact@example.com</p>
            </div>
          </div>
          <div class="info-card">
            <div class="info-icon">📞</div>
            <div class="info-details">
              <h3>전화번호</h3>
              <p>02-1234-5678</p>
            </div>
          </div>
          <div class="info-card">
            <div class="info-icon">📍</div>
            <div class="info-details">
              <h3>주소</h3>
              <p>서울시 강남구 테헤란로 123</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="contact-form-section">
        <h2>메시지 보내기</h2>
        <form @submit.prevent="submitForm" class="contact-form">
          <div class="form-group">
            <label for="name">이름</label>
            <input 
              type="text" 
              id="name" 
              v-model="form.name" 
              required
              :class="{ 'error': errors.name }"
            >
            <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
          </div>
          
          <div class="form-group">
            <label for="email">이메일</label>
            <input 
              type="email" 
              id="email" 
              v-model="form.email" 
              required
              :class="{ 'error': errors.email }"
            >
            <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
          </div>
          
          <div class="form-group">
            <label for="subject">제목</label>
            <input 
              type="text" 
              id="subject" 
              v-model="form.subject" 
              required
              :class="{ 'error': errors.subject }"
            >
            <span v-if="errors.subject" class="error-message">{{ errors.subject }}</span>
          </div>
          
          <div class="form-group">
            <label for="message">메시지</label>
            <textarea 
              id="message" 
              v-model="form.message" 
              rows="5" 
              required
              :class="{ 'error': errors.message }"
            ></textarea>
            <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
          </div>
          
          <button type="submit" class="submit-btn" :disabled="isSubmitting">
            <span v-if="isSubmitting">전송 중...</span>
            <span v-else>메시지 보내기</span>
          </button>
        </form>
        
        <div v-if="submitMessage" class="submit-message" :class="submitStatus">
          {{ submitMessage }}
        </div>
      </div>
      
      <div class="additional-info">
        <h2>운영 시간</h2>
        <div class="hours-grid">
          <div class="hours-item">
            <strong>평일</strong>
            <span>09:00 - 18:00</span>
          </div>
          <div class="hours-item">
            <strong>토요일</strong>
            <span>09:00 - 13:00</span>
          </div>
          <div class="hours-item">
            <strong>일요일</strong>
            <span>휴무</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      },
      errors: {},
      isSubmitting: false,
      submitMessage: '',
      submitStatus: ''
    }
  },
  methods: {
    validateForm() {
      this.errors = {}
      
      if (!this.form.name.trim()) {
        this.errors.name = '이름을 입력해주세요'
      }
      
      if (!this.form.email.trim()) {
        this.errors.email = '이메일을 입력해주세요'
      } else if (!this.isValidEmail(this.form.email)) {
        this.errors.email = '올바른 이메일 형식을 입력해주세요'
      }
      
      if (!this.form.subject.trim()) {
        this.errors.subject = '제목을 입력해주세요'
      }
      
      if (!this.form.message.trim()) {
        this.errors.message = '메시지를 입력해주세요'
      }
      
      return Object.keys(this.errors).length === 0
    },
    
    isValidEmail(email) {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
      return emailRegex.test(email)
    },
    
    async submitForm() {
      if (!this.validateForm()) {
        return
      }
      
      this.isSubmitting = true
      this.submitMessage = ''
      
      try {
        await new Promise(resolve => setTimeout(resolve, 1000))
        
        this.submitMessage = '메시지가 성공적으로 전송되었습니다!'
        this.submitStatus = 'success'
        
        this.form = {
          name: '',
          email: '',
          subject: '',
          message: ''
        }
      } catch (error) {
        this.submitMessage = '메시지 전송에 실패했습니다. 다시 시도해주세요.'
        this.submitStatus = 'error'
      } finally {
        this.isSubmitting = false
        setTimeout(() => {
          this.submitMessage = ''
        }, 5000)
      }
    }
  }
}
</script>

<style scoped>
.contact {
  min-height: 100vh;
  padding: 2rem 0;
}

.contact-header {
  text-align: center;
  padding: 2rem;
  background: linear-gradient(135deg, #00b894 0%, #00a085 100%);
  color: white;
  margin-bottom: 3rem;
}

.contact-header h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.contact-header p {
  font-size: 1.2rem;
  opacity: 0.9;
}

.contact-content {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 2rem;
}

.contact-info {
  margin-bottom: 3rem;
}

.contact-info h2 {
  font-size: 1.8rem;
  color: #2c3e50;
  margin-bottom: 1.5rem;
  border-bottom: 3px solid #00b894;
  padding-bottom: 0.5rem;
}

.info-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.info-card {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  display: flex;
  align-items: center;
  transition: transform 0.3s ease;
}

.info-card:hover {
  transform: translateY(-5px);
}

.info-icon {
  font-size: 2.5rem;
  margin-right: 1.5rem;
  background: #00b894;
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.info-details h3 {
  color: #2c3e50;
  margin-bottom: 0.5rem;
}

.info-details p {
  color: #666;
  margin: 0;
}

.contact-form-section {
  margin-bottom: 3rem;
}

.contact-form-section h2 {
  font-size: 1.8rem;
  color: #2c3e50;
  margin-bottom: 1.5rem;
  border-bottom: 3px solid #00b894;
  padding-bottom: 0.5rem;
}

.contact-form {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: #2c3e50;
  font-weight: 600;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.8rem;
  border: 2px solid #ddd;
  border-radius: 5px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #00b894;
}

.form-group input.error,
.form-group textarea.error {
  border-color: #e74c3c;
}

.error-message {
  color: #e74c3c;
  font-size: 0.9rem;
  margin-top: 0.25rem;
  display: block;
}

.submit-btn {
  background: #00b894;
  color: white;
  border: none;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  width: 100%;
}

.submit-btn:hover:not(:disabled) {
  background: #00a085;
}

.submit-btn:disabled {
  background: #ccc;
  cursor: not-allowed;
}

.submit-message {
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  font-weight: 600;
}

.submit-message.success {
  background: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.submit-message.error {
  background: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.additional-info h2 {
  font-size: 1.8rem;
  color: #2c3e50;
  margin-bottom: 1.5rem;
  border-bottom: 3px solid #00b894;
  padding-bottom: 0.5rem;
}

.hours-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.hours-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  border-left: 4px solid #00b894;
  background: #f8f9fa;
}

.hours-item strong {
  color: #2c3e50;
}

.hours-item span {
  color: #666;
}
</style>