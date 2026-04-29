# Lab4

[![Build Status](https://travis-ci.com/OlgaIAK/lab4.svg?branch=main)](https://travis-ci.com/OlgaIAK/lab4)

## Описание проекта
Проект содержит библиотеки и приложения для форматирования и решения квадратных уравнений.
# Отчет по лабораторной работе №4

**Студент:** Ольга  ИУ8-25
**Репозиторий:** https://github.com/OlgaIAK/lab4

## Выполненные действия

1. Репозиторий `lab4` создан на GitHub
2. Код из лабораторной работы №3 перенесен в репозиторий
3. Создан файл `.travis.yml` с конфигурацией для сборки на Linux (gcc и clang)
4. В `README.md` добавлен значок Travis CI
5. В репозитории присутствует `appveyor.yml` для сборки на Windows
6. Структура проекта сохранена (formatter_lib, formatter_ex_lib, solver_lib, приложения)

## Файлы конфигурации

### .travis.yml
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
