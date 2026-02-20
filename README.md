# autonomous_robot
# Autonomous 4-Wheel Robot Platform / Автономная роботизированная платформа с 4 колёсами

Author: Jay / Автор: Jay  
Status: Planning Phase / Статус: Этап планирования

---

## Project Goal / Цель проекта

Building a 4-wheel autonomous robot with:  
Создание 4-колёсного автономного робота с:

- Raspberry Pi (8GB) for Computer Vision & Quantized ML  
  Raspberry Pi (8GB) для компьютерного зрения и квантованных ML-моделей
- Arduino for motor control and ultrasonic sensing  
  Arduino для управления моторами и ультразвуковыми датчиками
- 3 fixed ultrasonic sensors (front, left [45 deg], right [45 deg])  
  3 фиксированными ультразвуковыми датчиками (спереди, слева [45°], справа [45°])
- CSI camera for live feed and object detection  
  CSI-камерой для видеопотока и обнаружения объектов
- Serial communication between Pi and Arduino  
  Последовательной связью между Pi и Arduino

---

## Architecture Overview / Обзор архитектуры

High-Level Brain / Высокоуровневый мозг:
- Raspberry Pi
- OpenCV
- TensorFlow Lite (INT8 quantized model)  
  TensorFlow Lite (INT8 квантованная модель)
- Navigation logic  
  Логика навигации

Low-Level Controller / Низкоуровневый контроллер:
- Arduino
- PWM motor control  
  PWM-управление моторами
- Ultrasonic sensor management  
  Управление ультразвуковыми датчиками
- Emergency safety override  
  Аварийное защитное отключение

---

## Design Philosophy / Философия проектирования

- Motors handled by Arduino for low-level machine control  
  Моторы управляются Arduino для низкоуровневого машинного контроля
- Ultrasonic safety overrides ML decisions  
  Ультразвуковая безопасность имеет приоритет над решениями ML
- System must fail safely  
  Система должна безопасно завершать работу при сбоях
- Modular design for future upgrades  
  Модульный дизайн для будущих обновлений

---

## Hardware / Аппаратное обеспечение

- Raspberry Pi 8GB
- Arduino Uno R3
- TB6612FNG motor driver  
  Драйвер моторов TB6612FNG
- 4 DC geared motors  
  4 редукторных DC-мотора
- 3x HC-SR04 ultrasonic sensors  
  3x ультразвуковых датчика HC-SR04
- Pi Camera (CSI)  
  Камера Pi (CSI)
- 2S Li-ion battery (7.4V)  
  2S Li-ion аккумулятор (7.4V)
- Buck converter (5V regulated)  
  Понижающий преобразователь (стабилизированные 5V)

---

## Features / Возможности

- Obstacle avoidance  
  Обход препятствий
- Person detection (quantized model)  
  Обнаружение человека (квантованная модель)
- Serial command protocol  
  Протокол последовательных команд
- Autonomous navigation state machine  
  Автономная навигация на основе конечного автомата

---

## Future Upgrades / Будущие обновления

- Inertial Measurement Unit (IMU) integration  
  Интеграция инерциального измерительного модуля (IMU)
- SLAM with Lidar  
  SLAM с использованием Lidar
- Web dashboard / Mobile App  
  Веб-панель управления / мобильное приложение
- Edge TPU acceleration for ML model  
  Аппаратное ускорение Edge TPU для ML-модели

---

## Project Roadmap / Дорожная карта проекта

### Phase 1 – Documentation / Фаза 1 – Документация
- [ ] System architecture / Архитектура системы
- [ ] Interfaces definition / Определение интерфейсов
- [ ] Pin mapping locked / Фиксация распиновки
- [ ] Power distribution plan / План распределения питания

### Phase 2 – Arduino Development / Фаза 2 – Разработка Arduino
- [ ] Motor control module / Модуль управления моторами
- [ ] Ultrasonic module / Ультразвуковой модуль
- [ ] Serial protocol implementation / Реализация последовательного протокола
- [ ] Safety timeout / Тайм-аут безопасности

### Phase 3 – Raspberry Pi Setup / Фаза 3 – Настройка Raspberry Pi
- [ ] Camera integration / Интеграция камеры
- [ ] TFLite object detection / Обнаружение объектов TFLite
- [ ] Serial communication / Последовательная связь

### Phase 4 – Integration / Фаза 4 – Интеграция
- [ ] End-to-end movement / Сквозное движение
- [ ] Obstacle avoidance / Обход препятствий
- [ ] Object-aware navigation / Навигация с учётом объектов

---


 
