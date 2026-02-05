<template>
<div class="app">
  <div class="card">
    <h1>⏱ ViserX Time Converter</h1>
    <p class="subtitle">
      60 minutes = <strong>0.5</strong>
    </p>

    <div class="input-group">
      <label>Minutes</label>
      <input
        type="number"
        v-model.number="minutes"
        placeholder="Enter minutes"
      />
    </div>

    <div v-if="minutes !== null" class="result">
      <span>Converted Value</span>
      <strong>{{ convertedTime }}</strong>
    </div>
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
/* Background */
.app {
min-height: 100vh;
background: linear-gradient(135deg, #667eea, #764ba2);
display: flex;
align-items: center;
justify-content: center;
font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

/* Card */
.card {
background: #ffffff;
padding: 28px;
border-radius: 14px;
width: 320px;
box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
text-align: center;
}

/* Headings */
h1 {
margin: 0;
font-size: 22px;
color: #333;
}

.subtitle {
margin: 8px 0 20px;
font-size: 14px;
color: #666;
}

/* Input */
.input-group {
text-align: left;
margin-bottom: 20px;
}

label {
font-size: 13px;
color: #555;
}

input {
width: 100%;
margin-top: 6px;
padding: 10px 12px;
font-size: 16px;
border-radius: 8px;
border: 1px solid #ddd;
outline: none;
transition: border 0.2s, box-shadow 0.2s;
}

input:focus {
border-color: #667eea;
box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.2);
}

/* Result */
.result {
background: #f4f6ff;
border-radius: 10px;
padding: 14px;
}

.result span {
display: block;
font-size: 13px;
color: #555;
}

.result strong {
font-size: 22px;
color: #667eea;
}
</style>
