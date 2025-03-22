# .github-workflows-ci-cd.yml
Create a CI/CD Pipeline
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2

      - name: Set up PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: '8.1'

      - name: Install Dependencies
        run: composer install

      - name: Run Tests
        run: php artisan test

  deploy:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to Preproduction
        run: echo "Déploiement en préproduction"
