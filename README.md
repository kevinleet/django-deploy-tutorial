# Django Project Deployment to Railway

In this tutorial, I'll walk you through the steps to deploy your Django project to Railway. Railway is a platform for deploying and managing web applications.

## Prerequisites

Before you begin, make sure you have the following prerequisites:

1. A Django project that you want to deploy.
2. Git installed on your local machine.
3. A Railway account. [Sign up for Railway](https://railway.app/) if you don't have one.

## Prepare Your Django Project

Follow the steps below to prepare your Django project for deployment:

1. ### Install gunicorn

   - In your project's root directory, run the following command: **pipenv install gunicorn**

     ![gunicorn](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/gunicorn.png?raw=true)

2. ### Create runtime.txt

   1. In your project's root directory, create a file named: **runtime.txt**
   2. Inside of the file, specify which version of Python to use. It is preferred to use the same version of Python that you're running locally.
   3. To check which version you are running virtually, type in your terminal: **python3 --version**
      ![runtime.txt](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/runtime.png?raw=true)

3. ### Allow Hosts and Trusted Origins

   In your settings.py file, update the following variables as pictured:

   - **ALLOWED_HOSTS = ['*']**

     ![allowedhosts](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/allowedhosts.png?raw=true)

   If you have a front end deployed that will access this Django deployment, add your front end url to the CSRF_TRUSTED_ORIGINS array:

   - **CSRF_TRUSTED_ORIGINS = ["http://yourfrontend.com"]**

     ![trustedorigins](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/trustedorigins.png?raw=true)

4. ### Install whitenoise

   **This step is only necessary if you are serving any static files from a framework, such as Django REST Framework. If you do not have static files to serve and are only deploying for REST API access, you can skip this step.**

   1. In your project's root directory, run the following command: **pipenv install whitenoise**
   2. In your settings.py file, add the following to the MIDDLEWARE section: **'whitenoise.middleware.WhiteNoiseMiddleware'**

      ![middleware](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/middleware.png?raw=true)

   3. In your settings.py file, add the following below the existing STATIC_URL line:

   - **STATIC_ROOT = os.path.join(BASE_DIR, 'static')**
   - **STATICFILES_STORAGE = 'whitenoise.storage.StaticFilesStorage'**

   ![static](https://github.com/kevinleet/django-deploy-tutorial/blob/main/images/static.png?raw=true)

   4. In your project's root directory, run the following command: **python3 manage.py collectstatic**

## Deploying to Railway

Congratulations! Your Django project is now ready for deployment. Follow the steps below to deploy your project to Railway:

### Step 1: Log in to Railway

Visit [Railway](https://railway.app/) and log in to your account.

### Step 2: Initialize Railway Project

If you haven't done this before, you'll need to initialize a new Railway project for your Django backend. Click on "New Project" and select your Git repository where your Django project is located.

### Step 3: Configure the Deployment

Once your project is initialized, you'll need to configure the deployment settings. Railway will automatically detect that you have a Python project and suggest the appropriate settings. Verify that the detected settings are correct and proceed.

### Step 4: Deploy Your Django Project

Click on the "Deploy" button, and Railway will begin the deployment process. You can monitor the progress in the Railway dashboard.

### Step 5: Access Your Deployed Django App

After the deployment is successful, Railway will provide you with a URL where your Django app is accessible. Click on the link, and your Django project is now live!

## Author

**Kevin Li**
[Github](https://github.com/kevinleet)
[LinkedIn](https://www.linkedin.com/in/kevinli617/)
