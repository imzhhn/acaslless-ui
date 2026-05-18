<template>
  <div class="login-container">
    <!-- 左侧品牌区域 -->
    <div class="brand-section">
      <div class="brand-content">
        <h1 class="brand-title">欢迎使用 ACASLLESS</h1>
        <p class="brand-slogan">安全、可靠、高效的解决方案</p>
        <div class="features">
          <div class="feature-item">
            <el-icon class="feature-icon"><Star /></el-icon>
            <span>简洁直观的界面设计</span>
          </div>
          <div class="feature-item">
            <el-icon class="feature-icon"><Star /></el-icon>
            <span>强大的数据安全保障</span>
          </div>
          <div class="feature-item">
            <el-icon class="feature-icon"><Star /></el-icon>
            <span>持续稳定的服务支持</span>
          </div>
        </div>
      </div>
      <div class="brand-decoration">
        <div class="circle circle-1"></div>
        <div class="circle circle-2"></div>
        <div class="circle circle-3"></div>
      </div>
    </div>

    <!-- 右侧表单区域 -->
    <div class="form-section">
      <div class="form-container">
        <!-- 标签切换 -->
        <div class="tab-header">
          <button
            :class="{ active: activeTab === 'login' }"
            @click="activeTab = 'login'"
          >
            登录
          </button>
          <button
            :class="{ active: activeTab === 'register' }"
            @click="activeTab = 'register'"
          >
            注册
          </button>
        </div>

        <!-- 登录表单 -->
        <transition name="fade-slide" mode="out-in">
          <form v-if="activeTab === 'login'" key="login" @submit.prevent="handleLogin">
            <h2 class="form-title">欢迎回来</h2>
            <p class="form-subtitle">请输入您的账户信息</p>

            <div class="input-group">
              <label for="login-email">邮箱</label>
              <div class="input-wrapper">
                <el-icon class="input-icon"><Message /></el-icon>
                <input
                  id="login-email"
                  v-model="loginForm.email"
                  type="email"
                  placeholder="请输入邮箱"
                  required
                />
              </div>
            </div>

            <div class="input-group">
              <label for="login-password">密码</label>
              <div class="input-wrapper">
                <el-icon class="input-icon"><Lock /></el-icon>
                <input
                  id="login-password"
                  v-model="loginForm.password"
                  :type="showPassword ? 'text' : 'password'"
                  placeholder="请输入密码"
                  required
                />
                <button
                  type="button"
                  class="toggle-password"
                  @click="showPassword = !showPassword"
                >
                  <el-icon><View v-if="!showPassword" /><Hide v-else /></el-icon>
                </button>
              </div>
            </div>

            <div class="form-options">
              <label class="remember-me">
                <input type="checkbox" v-model="loginForm.remember" />
                <span>记住我</span>
              </label>
              <a href="#" class="forgot-password">忘记密码？</a>
            </div>

            <button type="submit" class="submit-btn">登 录</button>

            <div class="divider">
              <span>或</span>
            </div>

            <div class="social-login">
              <button type="button" class="social-btn">
                <el-icon class="social-icon"><Globe /></el-icon>
                第三方登录
              </button>
            </div>
          </form>

          <!-- 注册表单 -->
          <form v-else key="register" @submit.prevent="handleRegister">
            <h2 class="form-title">创建账户</h2>
            <p class="form-subtitle">开始使用我们的服务</p>

            <div class="input-group">
              <label for="register-email">邮箱</label>
              <div class="input-wrapper">
                <el-icon class="input-icon"><Message /></el-icon>
                <input
                  id="register-email"
                  v-model="registerForm.email"
                  type="email"
                  placeholder="请输入邮箱"
                  required
                />
              </div>
            </div>

            <div class="input-group">
              <label for="register-password">密码</label>
              <div class="input-wrapper">
                <el-icon class="input-icon"><Lock /></el-icon>
                <input
                  id="register-password"
                  v-model="registerForm.password"
                  :type="showPassword ? 'text' : 'password'"
                  placeholder="请输入密码"
                  required
                />
                <button
                  type="button"
                  class="toggle-password"
                  @click="showPassword = !showPassword"
                >
                  <el-icon><View v-if="!showPassword" /><Hide v-else /></el-icon>
                </button>
              </div>
            </div>

            <label class="terms">
              <input type="checkbox" v-model="registerForm.agreeTerms" required />
              <span>我已阅读并同意 <a href="#">服务条款</a> 和 <a href="#">隐私政策</a></span>
            </label>

            <button type="submit" class="submit-btn">注 册</button>

            <div class="divider">
              <span>或</span>
            </div>

            <div class="social-login">
              <button type="button" class="social-btn">
                <el-icon class="social-icon"><Globe /></el-icon>
                第三方登录
              </button>
            </div>
          </form>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginRegister',
  data() {
    return {
      activeTab: 'login',
      showPassword: false,
      loginForm: {
        email: '',
        password: '',
        remember: false
      },
      registerForm: {
        email: '',
        password: '',
        agreeTerms: false
      }
    }
  },
  methods: {
    handleLogin() {
      console.log('登录信息:', this.loginForm)
      // TODO: 添加登录逻辑
    },
    handleRegister() {
      console.log('注册信息:', this.registerForm)
      // TODO: 添加注册逻辑
    }
  }
}
</script>

<style scoped>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.login-container {
  display: flex;
  width: 100vw;
  height: 100vh;
  background: #f8fafc;
}

/* 左侧品牌区域 */
.brand-section {
  flex: 1.5;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.brand-content {
  position: relative;
  z-index: 1;
  color: white;
  padding: 60px;
  text-align: left;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  min-height: 500px;
}

.brand-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 16px;
  letter-spacing: -0.5px;
}

.brand-slogan {
  font-size: 1.2rem;
  opacity: 0.9;
  margin-bottom: 48px;
}

.features {
  display: flex;
  flex-direction: column;
  gap: 20px;
  min-height: 120px;
}

.feature-item {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 1rem;
}

.feature-icon {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.9);
}

.brand-decoration {
  position: absolute;
  inset: 0;
  overflow: hidden;
}

.circle {
  position: absolute;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
}

.circle-1 {
  width: 400px;
  height: 400px;
  top: -100px;
  right: -100px;
}

.circle-2 {
  width: 300px;
  height: 300px;
  bottom: -50px;
  left: -50px;
}

.circle-3 {
  width: 200px;
  height: 200px;
  bottom: 100px;
  right: 100px;
}

/* 右侧表单区域 */
.form-section {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
}

.form-container {
  width: 100%;
  max-width: 360px;
}

/* 标签切换 */
.tab-header {
  display: flex;
  background: #e2e8f0;
  border-radius: 12px;
  padding: 4px;
  margin-bottom: 32px;
}

.tab-header button {
  flex: 1;
  padding: 12px 24px;
  border: none;
  background: transparent;
  font-size: 1rem;
  font-weight: 500;
  color: #64748b;
  cursor: pointer;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.tab-header button.active {
  background: white;
  color: #667eea;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

/* 表单样式 */
.form-title {
  font-size: 1.8rem;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 8px;
}

.form-subtitle {
  color: #64748b;
  margin-bottom: 32px;
}

.input-group {
  margin-bottom: 20px;
}

.input-group label {
  display: block;
  font-size: 0.875rem;
  font-weight: 500;
  color: #475569;
  margin-bottom: 8px;
}

.input-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.input-icon {
  position: absolute;
  left: 16px;
  font-size: 18px;
  color: #64748b;
  z-index: 1;
}

.input-wrapper input {
  width: 100%;
  padding: 14px 16px 14px 48px;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  transition: all 0.3s ease;
  outline: none;
  background: #f1f5f9;
}

.input-wrapper input:focus {
  box-shadow: 0 0 0 2px #667eea;
}

.input-wrapper input::placeholder {
  color: #94a3b8;
}

.toggle-password {
  position: absolute;
  right: 16px;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 18px;
  opacity: 0.6;
  color: #64748b;
  transition: opacity 0.3s;
}

.toggle-password:hover {
  opacity: 1;
}

/* 表单选项 */
.form-options {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
}

.remember-me,
.terms {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.875rem;
  color: #64748b;
  cursor: pointer;
}

.terms {
  margin-bottom: 20px;
}

.remember-me input,
.terms input {
  width: 18px;
  height: 18px;
  accent-color: #667eea;
  cursor: pointer;
}

.remember-me span {
  user-select: none;
}

.forgot-password {
  color: #667eea;
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
}

.forgot-password:hover {
  text-decoration: underline;
}

.terms a {
  color: #667eea;
  text-decoration: none;
}

.terms a:hover {
  text-decoration: underline;
}

/* 提交按钮 */
.submit-btn {
  width: 100%;
  padding: 14px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}

.submit-btn:active {
  transform: translateY(0);
}

/* 分隔符 */
.divider {
  display: flex;
  align-items: center;
  margin: 24px 0;
  color: #94a3b8;
  font-size: 0.875rem;
}

.divider::before,
.divider::after {
  content: '';
  flex: 1;
  height: 1px;
  background: #e2e8f0;
}

.divider span {
  padding: 0 16px;
}

/* 社交登录 */
.social-login {
  display: flex;
  gap: 12px;
}

.social-btn {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px;
  background: white;
  border: 2px solid #e2e8f0;
  border-radius: 10px;
  font-size: 0.9rem;
  font-weight: 500;
  color: #475569;
  cursor: pointer;
  transition: all 0.3s ease;
}

.social-btn:hover {
  border-color: #667eea;
  color: #667eea;
}

.social-icon {
  font-size: 18px;
}

/* 过渡动画 */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: all 0.3s ease;
}

.fade-slide-enter {
  opacity: 0;
  transform: translateX(20px);
}

.fade-slide-leave-to {
  opacity: 0;
  transform: translateX(-20px);
}

/* 响应式设计 */
@media (max-width: 968px) {
  .login-container {
    flex-direction: column;
  }

  .brand-section {
    padding: 60px 20px;
    min-height: auto;
  }

  .brand-content {
    padding: 20px;
    text-align: center;
  }

  .brand-title {
    font-size: 1.8rem;
  }

  .features {
    align-items: center;
  }

  .form-section {
    padding: 40px 20px;
  }
}

@media (max-width: 480px) {
  .tab-header button {
    padding: 10px 16px;
    font-size: 0.9rem;
  }

  .form-title {
    font-size: 1.5rem;
  }

  .social-login {
    flex-direction: column;
  }
}
</style>
