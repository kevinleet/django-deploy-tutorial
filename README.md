# Django Project Deployment to Railway

In this tutorial, we'll walk you through the steps to deploy your Django project to Railway. Railway is a platform for deploying and managing web applications.

## Prerequisites

Before you begin, make sure you have the following prerequisites:

1. A Django project that you want to deploy.
2. Git installed on your local machine.
3. A Railway account. [Sign up for Railway](https://railway.app/) if you don't have one.

## Prepare Your Django Project

Follow the steps below to prepare your Django project for deployment:

1. Install gunicorn

   - In your project's root directory, run the following command: **pipenv install gunicorn**

2. Create runtime.txt

   - In your project's root directory, create a file named: **runtime.txt**
   - Inside of the file, specify which version of Python to use. It is preferred to use the same version of Python that you're running locally.
     runtime.txt >>> **python -3.11.4**

   ![runtime.txt](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/runtime.png?raw=true)

   - To check which version you are running virtually, type in your terminal: **python3 --version**+
