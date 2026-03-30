# Exit Ticket Express — Implementation Plan
**Date:** 2026-03-30  
**Spec:** exit-ticket-express-spec.md  
**Estimated Time:** 2-3 hours  
**Output File:** `/tmp/teacher-tools/quick-poll/index.html`

---

## Phase 1: Modern CSS Design System (30 min)

### Task 1.1: Update CSS Variables & Base Styles
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Replace entire `<style>` section with modern design system:

```css
:root {
  --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --glass-bg: rgba(255, 255, 255, 0.95);
  --shadow-soft: 0 8px 32px rgba(0, 0, 0, 0.1);
  --shadow-elevated: 0 20px 60px rgba(0, 0, 0, 0.15);
  --radius-lg: 20px;
  --radius-md: 12px;
  --radius-sm: 8px;
  --transition-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
  --transition-smooth: cubic-bezier(0.4, 0, 0.2, 1);
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: var(--primary-gradient);
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  animation: gradientShift 15s ease infinite;
  background-size: 200% 200%;
}

@keyframes gradientShift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

.container {
  background: var(--glass-bg);
  backdrop-filter: blur(20px);
  border-radius: var(--radius-lg);
  padding: 40px;
  max-width: 800px;
  width: 100%;
  box-shadow: var(--shadow-elevated);
  border: 1px solid rgba(255, 255, 255, 0.2);
}
```

**Verification:** 
- [ ] Открыть файл в браузере
- [ ] Проверить анимированный градиент фона
- [ ] Убедиться что контейнер имеет glassmorphism эффект

---

### Task 1.2: Style Typography & Headers
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Add to CSS:

```css
h1 {
  text-align: center;
  font-size: 2.5rem;
  font-weight: 800;
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 10px;
  letter-spacing: -0.02em;
}

.subtitle {
  text-align: center;
  color: #666;
  font-size: 1.1rem;
  margin-bottom: 30px;
  font-weight: 500;
}

.section-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: #333;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
  gap: 10px;
}
```

**Verification:**
- [ ] Заголовок имеет gradient text effect
- [ ] Размеры и отступы корректны

---

### Task 1.3: Create Modern Preset Buttons
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Replace preset button styles:

```css
.presets {
  display: flex;
  gap: 12px;
  margin-bottom: 25px;
  flex-wrap: wrap;
  justify-content: center;
}

.preset-btn {
  padding: 15px 20px;
  border: none;
  background: white;
  border-radius: var(--radius-md);
  cursor: pointer;
  font-size: 1.5rem;
  transition: all 0.3s var(--transition-bounce);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  position: relative;
  overflow: hidden;
}

.preset-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--primary-gradient);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: 0;
}

.preset-btn:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.3);
}

.preset-btn.active {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
}

.preset-btn.active::before {
  opacity: 0.1;
}
```

**Verification:**
- [ ] Кнопки имеют bounce эффект при наведении
- [ ] Active state имеет фоновый градиент

---

### Task 1.4: Style Input Fields
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 3 min

```css
.question-input {
  width: 100%;
  padding: 18px 20px;
  border: 2px solid #e8e8e8;
  border-radius: var(--radius-md);
  font-size: 1.15rem;
  margin-bottom: 25px;
  font-family: inherit;
  transition: all 0.3s ease;
  background: white;
}

.question-input:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 4px rgba(102, 126, 234, 0.1);
}

.student-count-input {
  width: 120px;
  padding: 12px 15px;
  border: 2px solid #e8e8e8;
  border-radius: var(--radius-sm);
  font-size: 1.1rem;
  text-align: center;
  font-weight: 600;
}
```

**Verification:**
- [ ] Focus state имеет glow эффект
- [ ] Размеры comfortable для touch

---

### Task 1.5: Create 3D Voting Buttons
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 7 min

```css
.vote-buttons {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 20px;
  margin: 30px 0;
}

.vote-btn {
  padding: 35px 20px;
  font-size: 2.5rem;
  border: none;
  background: linear-gradient(145deg, #ffffff, #f0f0f0);
  border-radius: var(--radius-md);
  cursor: pointer;
  transition: all 0.2s var(--transition-bounce);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  box-shadow: 
    0 10px 20px rgba(0, 0, 0, 0.1),
    inset 0 2px 0 rgba(255, 255, 255, 0.8),
    inset 0 -4px 0 rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
}

.vote-btn::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.vote-btn:hover {
  transform: translateY(-5px) scale(1.02);
  box-shadow: 
    0 15px 30px rgba(0, 0, 0, 0.15),
    inset 0 2px 0 rgba(255, 255, 255, 0.8),
    inset 0 -4px 0 rgba(0, 0, 0, 0.1);
}

.vote-btn:active {
  transform: translateY(-2px) scale(0.98);
  box-shadow: 
    0 5px 10px rgba(0, 0, 0, 0.1),
    inset 0 2px 5px rgba(0, 0, 0, 0.1);
}

.vote-btn:active::after {
  width: 300px;
  height: 300px;
}

.vote-btn .label {
  font-size: 1rem;
  font-weight: 700;
  color: #333;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.vote-btn.voted {
  background: linear-gradient(145deg, #d4edda, #c3e6cb);
  box-shadow: 
    0 5px 15px rgba(40, 167, 69, 0.3),
    inset 0 2px 0 rgba(255, 255, 255, 0.5);
  animation: votePulse 0.5s ease;
}

@keyframes votePulse {
  0% { transform: scale(1); }
  50% { transform: scale(0.95); }
  100% { transform: scale(1); }
}
```

**Verification:**
- [ ] Кнопки имеют 3D эффект с тенями
- [ ] Ripple effect при нажатии
- [ ] Hover поднимает кнопку

---

### Task 1.6: Style Progress & Counter
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

```css
.counter-section {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
  border-radius: var(--radius-md);
  padding: 25px;
  margin: 25px 0;
  text-align: center;
  border: 2px solid #e9ecef;
}

.counter-text {
  font-size: 1.4rem;
  font-weight: 700;
  color: #333;
  margin-bottom: 15px;
}

.counter-numbers {
  font-size: 2.5rem;
  font-weight: 800;
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.voting-progress {
  width: 100%;
  height: 12px;
  background: #e9ecef;
  border-radius: 10px;
  overflow: hidden;
  margin-top: 15px;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
}

.voting-progress-fill {
  height: 100%;
  background: var(--primary-gradient);
  border-radius: 10px;
  transition: width 0.5s var(--transition-smooth);
  box-shadow: 0 2px 10px rgba(102, 126, 234, 0.4);
}
```

**Verification:**
- [ ] Counter имеет gradient text
- [ ] Progress bar анимированный

---

## Phase 2: Blind Voting System (20 min)

### Task 2.1: Add Student Count Input to Setup
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Add to HTML setup section:

```html
<div class="setup-field">
  <label class="field-label">👥 Количество учеников в классе:</label>
  <input type="number" class="student-count-input" id="studentCount" 
         value="25" min="1" max="50">
</div>
```

Add CSS:

```css
.setup-field {
  margin-bottom: 25px;
}

.field-label {
  display: block;
  font-weight: 600;
  color: #333;
  margin-bottom: 10px;
  font-size: 1rem;
}
```

**Verification:**
- [ ] Поле видно и редактируется
- [ ] Мин/макс работают

---

### Task 2.2: Update JavaScript for Blind Voting
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 10 min

Update JS logic:

```javascript
let expectedCount = 25;
let resultsRevealed = false;

function startVoting() {
  expectedCount = parseInt(document.getElementById('studentCount').value) || 25;
  resultsRevealed = false;
  
  // ... existing code ...
  
  // Show voting section with blind mode
  document.getElementById('setupSection').style.display = 'none';
  document.getElementById('votingSection').style.display = 'block';
  document.getElementById('resultsSection').style.display = 'none'; // Hide results initially
  document.getElementById('revealButton').style.display = 'block'; // Show reveal button
  
  updateBlindDisplay();
}

function castVote(option) {
  votes[option.label]++;
  totalVotes++;
  
  // Visual feedback
  event.target.classList.add('voted');
  setTimeout(() => event.target.classList.remove('voted'), 300);
  
  playSound();
  updateBlindDisplay();
  
  // Auto-reveal if everyone voted
  if (totalVotes >= expectedCount) {
    setTimeout(() => revealResults(), 500);
  }
}

function updateBlindDisplay() {
  document.getElementById('voteCount').textContent = totalVotes;
  document.getElementById('expectedCount').textContent = expectedCount;
  
  const progressPercent = (totalVotes / expectedCount) * 100;
  document.getElementById('votingProgressFill').style.width = progressPercent + '%';
}

function revealResults() {
  resultsRevealed = true;
  document.getElementById('resultsSection').style.display = 'block';
  document.getElementById('revealButton').style.display = 'none';
  
  // Animate results
  const resultsSection = document.getElementById('resultsSection');
  resultsSection.innerHTML = '';
  resultsSection.style.opacity = '0';
  
  currentPreset.options.forEach((option, index) => {
    setTimeout(() => {
      const count = votes[option.label] || 0;
      const percentage = totalVotes > 0 ? (count / totalVotes * 100).toFixed(0) : 0;
      
      const bar = document.createElement('div');
      bar.className = 'result-bar';
      bar.style.animation = 'slideIn 0.5s ease forwards';
      bar.style.animationDelay = (index * 0.1) + 's';
      bar.innerHTML = `
        <div class="result-header">
          <span class="result-emoji">${option.emoji}</span>
          <span class="result-label-text">${option.label}</span>
        </div>
        <div class="result-bar-bg">
          <div class="result-fill" style="width: 0%; background: ${option.color};">
            <span class="result-count">${count}</span>
          </div>
        </div>
        <div class="result-percentage">${percentage}%</div>
      `;
      resultsSection.appendChild(bar);
      
      // Animate fill
      setTimeout(() => {
        bar.querySelector('.result-fill').style.width = percentage + '%';
      }, 100);
    }, index * 100);
  });
  
  resultsSection.style.transition = 'opacity 0.5s ease';
  resultsSection.style.opacity = '1';
}
```

**Verification:**
- [ ] Ввод количества учеников работает
- [ ] Результаты скрыты до нажатия кнопки
- [ ] Прогресс-бар показывает процент голосов

---

### Task 2.3: Create Animated Results Bars
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Add CSS for animated results:

```css
.results-section {
  margin-top: 30px;
  padding: 25px;
  background: white;
  border-radius: var(--radius-md);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.result-bar {
  margin-bottom: 20px;
  opacity: 0;
  transform: translateX(-20px);
}

@keyframes slideIn {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.result-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 8px;
}

.result-emoji {
  font-size: 1.5rem;
}

.result-label-text {
  font-weight: 600;
  color: #333;
  font-size: 1.1rem;
}

.result-bar-bg {
  height: 35px;
  background: #e9ecef;
  border-radius: 18px;
  overflow: hidden;
  position: relative;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
}

.result-fill {
  height: 100%;
  border-radius: 18px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  padding-right: 15px;
  transition: width 1s var(--transition-smooth);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.result-count {
  color: white;
  font-weight: 700;
  font-size: 1rem;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

.result-percentage {
  text-align: right;
  font-weight: 700;
  color: #666;
  font-size: 1.1rem;
  margin-top: 5px;
}
```

**Verification:**
- [ ] Результаты появляются с анимацией slideIn
- [ ] Бары заполняются плавно
- [ ] Проценты отображаются

---

## Phase 3: Control Buttons & Polish (10 min)

### Task 3.1: Style Control Buttons
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

```css
.controls {
  display: flex;
  gap: 15px;
  justify-content: center;
  margin-top: 30px;
  flex-wrap: wrap;
}

.control-btn {
  padding: 16px 32px;
  font-size: 1.05rem;
  border: none;
  border-radius: var(--radius-md);
  cursor: pointer;
  font-weight: 700;
  transition: all 0.3s var(--transition-bounce);
  text-transform: uppercase;
  letter-spacing: 0.5px;
  position: relative;
  overflow: hidden;
}

.btn-start {
  background: var(--primary-gradient);
  color: white;
  box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
}

.btn-start:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 35px rgba(102, 126, 234, 0.5);
}

.btn-reveal {
  background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
  color: white;
  box-shadow: 0 8px 25px rgba(40, 167, 69, 0.4);
  font-size: 1.2rem;
  padding: 20px 40px;
}

.btn-reveal:hover {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 12px 35px rgba(40, 167, 69, 0.5);
}

.btn-reset {
  background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
  color: white;
  box-shadow: 0 8px 25px rgba(231, 76, 60, 0.4);
}

.btn-reset:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 35px rgba(231, 76, 60, 0.5);
}
```

**Verification:**
- [ ] Все кнопки имеют градиенты и тени
- [ ] Hover эффекты работают

---

### Task 3.2: Add Sound Effects
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 3 min

Update sound function:

```javascript
function playSound(type = 'vote') {
  try {
    const audioContext = new (window.AudioContext || window.webkitAudioContext)();
    const oscillator = audioContext.createOscillator();
    const gainNode = audioContext.createGain();
    
    oscillator.connect(gainNode);
    gainNode.connect(audioContext.destination);
    
    if (type === 'vote') {
      // Pleasant "ding"
      oscillator.frequency.setValueAtTime(880, audioContext.currentTime);
      oscillator.frequency.exponentialRampToValueAtTime(440, audioContext.currentTime + 0.1);
      gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
      gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.3);
      oscillator.start(audioContext.currentTime);
      oscillator.stop(audioContext.currentTime + 0.3);
    } else if (type === 'reveal') {
      // Victory sound
      oscillator.frequency.setValueAtTime(523.25, audioContext.currentTime);
      oscillator.frequency.setValueAtTime(659.25, audioContext.currentTime + 0.1);
      oscillator.frequency.setValueAtTime(783.99, audioContext.currentTime + 0.2);
      gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
      gainNode.gain.linearRampToValueAtTime(0, audioContext.currentTime + 0.6);
      oscillator.start(audioContext.currentTime);
      oscillator.stop(audioContext.currentTime + 0.6);
    }
  } catch(e) {
    // Audio not supported
  }
}
```

**Verification:**
- [ ] Звук при голосовании
- [ ] Звук при раскрытии результатов

---

### Task 3.3: Add Fullscreen Button
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 2 min

Already exists in code, verify it works and add styling:

```css
.fullscreen-btn {
  position: fixed;
  top: 20px;
  right: 20px;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border: none;
  padding: 12px 16px;
  border-radius: var(--radius-sm);
  cursor: pointer;
  font-size: 1.3rem;
  z-index: 1000;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.fullscreen-btn:hover {
  transform: scale(1.1);
  background: white;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
}
```

**Verification:**
- [ ] Кнопка fullscreen работает
- [ ] Hover эффект есть

---

## Phase 4: Final Integration & Testing (10 min)

### Task 4.1: Assemble Complete HTML
**File:** `/tmp/teacher-tools/quick-poll/index.html`  
**Time:** 5 min

Ensure all pieces are integrated:
- CSS in `<style>`
- HTML structure with blind voting elements
- JavaScript with all functions
- No conflicts between old and new code

**Verification:**
- [ ] Файл открывается без ошибок
- [ ] Консоль браузера чистая (нет ошибок JS)

---

### Task 4.2: Test Complete Flow
**Time:** 5 min

Test manually:
1. Открыть файл в браузере
2. Выбрать preset
3. Изменить количество учеников
4. Нажать "Начать"
5. Проголосовать несколько раз
6. Убедиться что результаты скрыты
7. Нажать "Показать результаты"
8. Проверить анимацию
9. Нажать "Новый опрос"
10. Проверить что всё сбросилось

---

## Verification Checklist

- [ ] Дизайн современный, градиенты анимированы
- [ ] Кнопки имеют 3D эффект и ripple
- [ ] Шрифты читаемые, hierarchy ясная
- [ ] Результаты скрыты до нажатия кнопки
- [ ] Счётчик показывает X / Y
- [ ] Прогресс-бар работает
- [ ] Анимация результатов плавная
- [ ] Звуки работают
- [ ] Fullscreen работает
- [ ] Mobile responsive

---

## Git Workflow

After all tasks complete:

```bash
cd /tmp/teacher-tools/quick-poll
git add .
git commit -m "Complete redesign: modern UI + blind voting system"
git push
```

---

**Plan complete! Ready for execution?** 🚀
