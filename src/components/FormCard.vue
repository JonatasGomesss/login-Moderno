<template>
  <v-container class="total pa-0 ma-0" fluid>
    <div class="bg-decoration">
      <div class="orb orb-1" />
      <div class="orb orb-2" />
    </div>

    <form class="form-card" @submit.prevent>
      <div class="form-header">
        <h1 class="form-title">Entrar</h1>
        <p class="form-subtitle">Bem-vindo de volta</p>
      </div>

      <div class="form-fields">
        <div class="field-group">
          <label class="field-label" for="email">Email</label>
          <div class="input-wrapper">
            <input
              id="email"
              v-model="email"
              class="field-input"
              placeholder="seu@email.com"
              type="email"
            >
            <span class="input-line" />
          </div>
        </div>

        <div class="field-group">
          <label class="field-label" for="senha">Senha</label>
          <div class="input-wrapper">
            <input
              id="senha"
              v-model="password"
              class="field-input"
              placeholder="sua senha"
              :type="showPassword ? 'text' : 'password'"
            >
            <button
              class="toggle-password"
              tabindex="-1"
              type="button"
              @click="showPassword = !showPassword"
            >
              {{ showPassword ? visivel : '🔒' }}
            </button>
            <span class="input-line" />
          </div>
        </div>

        <div class="forgot-row">
          <a class="forgot-link" href="#">Esqueceu a senha?</a>
        </div>
      </div>

      <div class="form-actions">
        <button class="btn-primary" type="submit">
          <span class="btn-arrow">Entrar ➜</span>
        </button>

        <div class="divider">
          <span />
          <small>ou</small>
          <span />
        </div>

        <router-link class="btn-secondary" to="/NavBar">
          Criar conta
        </router-link>
      </div>
    </form>
  </v-container>
</template>

<script setup>
  import { ref } from 'vue'
  import { useRouter } from 'vue-router'

  const visivel = ref('🔓')
  const email = ref('')
  const password = ref('')
  const showPassword = ref(false)

  const router = useRouter()

  function irParaCriarConta () {
    router.push('/NavBar')
  }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500&family=DM+Sans:wght@300;400&display=swap');

/* ── Variáveis ── */
/* Troca :root por .total */
.total {
  --bg: #0a0a0b;
  --surface: #111113;
  --border: rgba(255, 255, 255, 0.07);
  --border-focus: rgba(255, 255, 255, 0.3);
  --text: #f0ede8;
  --text-muted: rgba(240, 237, 232, 0.4);
  --accent: #c9a96e;
  --accent-glow: rgba(201, 169, 110, 0.15);

  /* restante do estilo do .total */
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #0a0a0b;
  font-family: 'DM Sans', sans-serif;
  overflow: hidden;
  position: relative;
}
/* ── Layout ── */
.total {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #0a0a0b;
  font-family: 'DM Sans', sans-serif;
  overflow: hidden;
  position: relative;
}

/* ── Decoração de fundo ── */
.bg-decoration {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.18;
}

.orb-1 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, #c9a96e 0%, transparent 70%);
  top: -100px;
  right: -80px;
  animation: drift 8s ease-in-out infinite alternate;
}

.orb-2 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, #7b9cbe 0%, transparent 70%);
  bottom: -80px;
  left: -60px;
  animation: drift 10s ease-in-out infinite alternate-reverse;
}

@keyframes drift {
  from { transform: translate(0, 0); }
  to   { transform: translate(20px, 20px); }
}

/* ── Card ── */
.form-card {
  position: relative;
  width: 100%;
  max-width: 400px;
  padding: 52px 48px;
  background: var(--surface);
  border: 1px solid var(--border);
  box-shadow:
    0 0 0 10px rgba(34, 46, 82, 0.03),
    0 40px 60px rgba(57, 55, 55, 0.6);
  animation: fadeUp 0.6s cubic-bezier(0.16, 1, 0.3, 1) both;
}

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ── Header ── */
.form-header {
  text-align: center;
  margin-bottom: 44px;
}

.logo-mark {
  font-size: 18px;
  color: var(--accent);
  margin-bottom: 20px;
  display: block;
  opacity: 0.9;
  letter-spacing: 4px;
}

.form-title {
  font-family: 'Cormorant Garamond', serif;
  font-weight: 500;
  font-size: 2.4rem;
  color: var(--text);
  margin: 0 0 6px;
  letter-spacing: 0.04em;
}

.form-subtitle {
  font-size: 0.8rem;
  color: var( --accent);
  letter-spacing: 0.08em;
  text-transform: uppercase;
  margin: 0;
  font-weight: 300;
}

/* ── Campos ── */
.form-fields {
  display: flex;
  flex-direction: column;
  gap: 28px;
  margin-bottom: 36px;
}

.field-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.field-label {
  font-size: 0.7rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var( --accent);
  font-weight: 400;
  transition: color 0.3s ease;
}

.field-group:focus-within .field-label {
  color: var(--accent);
}

.input-wrapper {
  position: relative;
}

.field-input {
  width: 100%;
  background: transparent;
  border: none;
  border-bottom: 1px solid var(--border);
  padding: 10px 0;
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
  font-size: 0.95rem;
  font-weight: 300;
  outline: none;
  transition: border-color 0.3s ease;
  box-sizing: border-box;
}

.field-input::placeholder {
  color: rgba(240, 237, 232, 0.18);
}

.field-input:focus {
  border-bottom-color: transparent;
}

/* Linha animada no foco */
.input-line {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 1px;
  background: var(--accent);
  transition: width 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  pointer-events: none;
}

.input-wrapper:focus-within .input-line {
  width: 100%;
}

.toggle-password {
  position: absolute;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  color: var(--text-muted);
  cursor: pointer;
  font-size: 0.85rem;
  padding: 4px;
  transition: color 0.2s ease;
}

.toggle-password:hover {
  color: var(--accent);
}

/* ── Esqueceu senha ── */
.forgot-row {
  display: flex;
  justify-content: flex-end;
  margin-top: -8px;
}

.forgot-link {
  font-size: 0.72rem;
  color: var(--text-muted);
  text-decoration: none;
  letter-spacing: 0.04em;
  transition: color 0.2s ease;
}

.forgot-link:hover {
  color: var(--accent);
}

/* ── Botões ── */
.form-actions {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.btn-primary {
  width: 100%;
  padding: 14px 24px;
  background: transparent;
  border: var(--accent);
  border-radius: 1px;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.btn-primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: var(--accent);
  transform: translateX(-100%);
  transition: transform 0.4s ease;
}

.btn-primary:hover::before {
  transform: translateX(0);
}

.btn-primary:hover {
  box-shadow: 0 8px 24px var(--accent-glow);
}

.btn-arrow {
color:#ffffff;
margin: auto;
  font-size: 1rem;
  transition: transform 0.3s ease;
}

.btn-primary:hover .btn-arrow {
  transform: translateX(4px);
}

/* ── Divisor ── */
.divider {
  display: flex;
  align-items: center;
  gap: 12px;
}

.divider span {
  flex: 1;
  height: 1px;
  background: var(--border);
}

.divider small {
  font-size: 0.68rem;
  color: var(--text-muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.btn-secondary {
  width: 100%;
  padding: 13px 24px;
  background: transparent;
  border: 1px solid var(--accent);
  color: var(--accent);
  font-family: 'DM Sans', sans-serif;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  cursor: pointer;
  text-decoration: none;
  display: block;
  text-align: center;
  box-sizing: border-box;
  transition: background 0.3s ease, color 0.3s ease, box-shadow 0.3s ease;
}

.btn-secondary:hover {
  background: var(--accent);
  color: #0a0a0b;
  box-shadow: 0 8px 24px var(--accent-glow);
}
</style>
