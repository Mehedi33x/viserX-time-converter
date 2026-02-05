<template>
  
    <div class="card">
      <h1>⏱ ViserX Time Converter</h1>
      <p class="subtitle">
        60 minutes = <strong>0.5</strong>
      </p>

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
      // Assuming your real formula is minutes → some decimal value
      // Current formula seemed possibly incorrect → adjusted example
      return (this.minutes * 0.5 / 60).toFixed(4);
      // Alternative examples people often use:
      // return (this.minutes / 60).toFixed(2) + ' hours';
      // return (this.minutes * 0.0166667).toFixed(4);
    }
  }
};
</script>

<style>
.app {
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  font-family: "Segoe UI", system-ui, -apple-system, sans-serif;
}

.card {
  background: white;
  padding: 2.8rem 2.4rem;
  border-radius: 16px;
  width: 100%;
  max-width: 420px;          /* mobile default */
  box-shadow: 
    0 20px 40px rgba(0,0,0,0.18),
    0 8px 20px rgba(0,0,0,0.12);
  text-align: center;
  transition: all 0.25s ease;
}

/* ── Desktop adjustments ─────────────────────────────── */
@media (min-width: 640px) {
  .card {
    max-width: 480px;
    padding: 3.2rem 3rem;
    border-radius: 20px;
    box-shadow: 
      0 30px 60px rgba(0,0,0,0.2),
      0 10px 30px rgba(0,0,0,0.12);
  }

  h1 {
    font-size: 2.1rem;
  }

  .subtitle {
    font-size: 1.05rem;
    margin: 0.8rem 0 2.2rem;
  }

  .input-group label {
    font-size: 0.95rem;
  }

  input {
    font-size: 1.25rem;
    padding: 14px 16px;
  }

  .result {
    padding: 1.4rem;
    margin-top: 1.8rem;
  }

  .result span {
    font-size: 0.9rem;
  }

  .result strong {
    font-size: 2.4rem;
  }
}

/* ── Typography & colors ── */
h1 {
  margin: 0;
  font-size: 1.75rem;
  font-weight: 600;
  color: #1f2937;
}

.subtitle {
  margin: 0.6rem 0 1.8rem;
  font-size: 0.95rem;
  color: #64748b;
}

.subtitle strong {
  color: #4f46e5;
}

.input-group {
  text-align: left;
  margin-bottom: 1.8rem;
}

label {
  font-size: 0.85rem;
  font-weight: 500;
  color: #475569;
  display: block;
  margin-bottom: 0.5rem;
}

input {
  width: 100%;
  padding: 12px 14px;
  font-size: 1.1rem;
  border: 1px solid #d1d5db;
  border-radius: 10px;
  outline: none;
  transition: all 0.2s ease;
  box-sizing: border-box;
}

input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.15);
}

.result {
  background: #f8fafc;
  border-radius: 12px;
  padding: 1.2rem;
  margin-top: 1.4rem;
  transition: all 0.2s ease;
}

.result span {
  display: block;
  font-size: 0.8rem;
  color: #64748b;
  margin-bottom: 0.4rem;
}

.result strong {
  font-size: 1.9rem;
  color: #6366f1;
  letter-spacing: -0.5px;
}

.result.error {
  background: #fef2f2;
  color: #ef4444;
  font-weight: 500;
  padding: 1rem;
}

/* Very small screens */
@media (max-width: 360px) {
  .card {
    padding: 1.8rem 1.4rem;
  }
}
</style>