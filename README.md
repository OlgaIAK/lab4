# Lab4

[![Build Status](https://travis-ci.com/OlgaIAK/lab4.svg?branch=main)](https://travis-ci.com/OlgaIAK/lab4)

## Описание проекта
Проект содержит библиотеки и приложения для форматирования и решения квадратных уравнений.

---

# Отчет по лабораторной работе №4

**Студент:** Ольга (ИУ8-25)  
**Репозиторий:** [https://github.com/OlgaIAK/lab4](https://github.com/OlgaIAK/lab4)

## Цель работы
Научиться настраивать системы непрерывной интеграции (Continuous Integration, CI) для C++ проекта на примере сервисов **Travis CI** (Linux) и **AppVeyor** (Windows).

## Выполненные действия

1.  **Подготовка репозитория:**
    *   Репозиторий `lab4` создан на GitHub.
    *   Код из предыдущей лабораторной работы №3 (библиотеки `formatter_lib`, `formatter_ex_lib`, `solver_lib` и приложения) перенесен в репозиторий.

2.  **Настройка Travis CI (сборка на Linux):**
    *   В корне репозитория создан файл конфигурации `.travis.yml`.
    *   Настроена сборка с использованием компиляторов `gcc` и `clang`.
    *   В файл `README.md` добавлен **значок статуса сборки** (см. шапку отчета).

3.  **Настройка AppVeyor (сборка на Windows):**
    *   В репозитории присутствует файл конфигурации `appveyor.yml`.
    *   Он настроен для сборки проекта на платформах `x64` и `x86` в конфигурациях `Debug` и `Release`.

4.  **Оформление отчета:**
    *   Все выполненные шаги и файлы конфигурации задокументированы в этом отчете (файл `README.md`).

## Файлы конфигурации

### 1. `.travis.yml` (Linux, gcc/clang)
```yaml
language: cpp
compiler:
  - gcc
  - clang
addons:
  apt:
    sources: [george-edison55-precise-backports]
    packages: [cmake, cmake-data]
script:
  - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
  - cmake --build _build
  - cmake --build _build --target install
  version: 1.0.{build}
image: Visual Studio 2017

platform:
  - x64
  - x86

configuration:
  - Debug
  - Release

build_script:
  - mkdir build
  - cd build
  - cmake .. -G "Visual Studio 15 2017" -A %PLATFORM%
  - cmake --build . --config %CONFIGURATION%
