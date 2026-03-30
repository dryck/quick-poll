# Exit Ticket Express — Spec
**Date:** 2026-03-30  
**Status:** Draft — Awaiting confirmation

---

## 🎯 Objective
Улучшить Exit Ticket Express: современный дизайн + слепое голосование

---

## 📋 Requirements

### Feature 1: Frontend Design Improvements

| Element | Current | Target |
|---------|---------|--------|
| **Colors** | Basic gradients | Modern palette, better contrast |
| **Animations** | Basic hover | Smooth transitions, micro-interactions |
| **Typography** | System fonts | Better hierarchy, readable sizes |
| **Buttons** | Simple borders | Neumorphism/glassmorphism, tactile feel |
| **Results** | Plain bars | Animated progress bars with icons |

**Specific improvements:**
- ✅ Gradient backgrounds с анимацией
- ✅ Кнопки с 3D-эффектом при нажатии
- ✅ Плавные переходы между состояниями
- ✅ Улучшенная типографика (заголовки, контраст)
- ✅ Анимация заполнения результатов
- ✅ Glow-эффекты для активных элементов

### Feature 2: Blind Voting System

**Flow:**
1. Учитель настраивает опрос
2. Учитель видит: "Проголосовало: X / Y" (Y = ожидаемое количество)
3. Учитель видит прогресс-бар голосования (без распределения по ответам)
4. Когда все проголосовали (или учитель решает) — жмёт "Показать результаты"
5. Появляется красивая визуализация с распределением голосов

**UI Elements:**
- Поле ввода "Количество учеников в классе" (по умолчанию 25)
- Прогресс-бар "Голосование идёт..."
- Счётчик "Проголосовало: X / Y"
- Кнопка "Показать результаты" (активна когда X = Y или сразу)
- Красивое раскрытие результатов (анимация)

---

## 🎨 Design Inspiration

**Style:** Modern, playful, teacher-friendly  
**Colors:** Soft gradients, purple/blue primary, green/yellow/red for responses  
**Animations:** Spring physics, staggered reveals  
**Typography:** Clean sans-serif, strong hierarchy

---

## ✅ Acceptance Criteria

- [ ] Дизайн выглядит современно и профессионально
- [ ] Анимации плавные (60fps)
- [ ] Результаты скрыты до нажатия кнопки
- [ ] Учитель видит прогресс голосования
- [ ] Работает на мобильных и планшетах
- [ ] Звуковой feedback при голосовании

---

## ❌ Out of Scope

- Backend / сервер
- Авторизация / логин
- Сохранение истории опросов
- Экспорт результатов
- QR-коды

---

## 📁 Files to Modify

- `/tmp/teacher-tools/quick-poll/index.html` — полная переработка

---

**Подтверждаем spec?** Есть изменения?
