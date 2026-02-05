<template>
    <div class="card">
      <h1>⏱Story Point Converter ViserX</h1>

      <div class="input-group">
        <label for="minutes-input">Minutes</label>
        <input
          id="minutes-input"
          type="number"
          v-model.number="minutes"
          placeholder="Enter minutes"
          step="any"
        />
      </div>

      <div v-if="minutes !== null && !isNaN(minutes)" class="result">
        <span>Converted Value</span>
        <strong>{{ convertedTime }}</strong>
      </div>

      <div v-else-if="minutes !== null" class="result error">
        Please enter a valid number
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      minutes: null
    };
  },
  computed: {
    convertedTime() {
      return (this.minutes * 0.5 / 60).toFixed(4);
    }
  }
};
</script>

<style>
/* Ensure full-height desktop centering */
html,
body {
  height: 100%;
  margin: 0;
  font-family: "Segoe UI", system-ui, -apple-system, sans-serif;
}

.app {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

/* Desktop-only card */
.card {
  background: white;
  margin-left: 314px;  /* desktop left margin */
  width: 560px;              /* fixed desktop width */
  padding: 3.2rem 3rem;
  border-radius: 20px;
  text-align: center;
  box-shadow:
    0 30px 60px rgba(0,0,0,0.2),
    0 10px 30px rgba(0,0,0,0.12);
}

/* Typography */
h1 {
  margin: 0;
  font-size: 2.1rem;
  font-weight: 600;
  color: #1f2937;
}

.input-group {
  text-align: left;
  margin: 2rem 0;
}

label {
  font-size: 0.95rem;
  font-weight: 500;
  color: #475569;
  display: block;
  margin-bottom: 0.5rem;
}

input {
  width: 100%;
  padding: 14px 16px;
  font-size: 1.25rem;
  border: 1px solid #d1d5db;
  border-radius: 10px;
  outline: none;
  box-sizing: border-box;
  transition: all 0.2s ease;
}

input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.15);
}

/* Result */
.result {
  background: #f8fafc;
  border-radius: 12px;
  padding: 1.4rem;
  margin-top: 1.8rem;
}

.result span {
  display: block;
  font-size: 0.9rem;
  color: #64748b;
  margin-bottom: 0.4rem;
}

.result strong {
  font-size: 2.4rem;
  color: #6366f1;
  letter-spacing: -0.5px;
}

.result.error {
  background: #fef2f2;
  color: #ef4444;
  font-weight: 500;
}
</style>
