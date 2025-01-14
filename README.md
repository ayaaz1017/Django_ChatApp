# Real-Time Chat App with AWS Integration

Welcome to the **Real-Time Chat App**! This app allows users to chat in real time, upload files to AWS S3, and even includes a fun AWS Lambda function to add numbers. Let's get you started with setting it up and using it.

---

## Features

### Chat Functionality
- Real-time messaging using WebSockets.
- Chat history stored and retrieved from the database.
- User authentication (sign-up and log-in included).

### AWS Integration
- **S3 Upload**: Upload files (e.g., PDFs, documents) securely to an S3 bucket.
- **Lambda Function**: Add two numbers via an AWS Lambda function.

### Responsive Design
- Works across devices with a user-friendly interface.

---

## Setting Up the Project

### Step 1: Clone the Repository
```bash
git clone https://github.com/your-repo/chat-app.git
cd chat-app
```

### Step 2: Create a Virtual Environment
Set up a Python virtual environment to manage dependencies:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 3: Install Dependencies
Install all required Python packages:
```bash
pip install -r requirements.txt
```

### Step 4: Configure AWS
Create an `.env` file in the root directory with the following content:
```env
AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
AWS_REGION_NAME=your-region
AWS_S3_BUCKET_NAME=your-bucket-name
```
Replace `your-access-key`, `your-secret-key`, `your-region`, and `your-bucket-name` with your actual AWS credentials and bucket name.

### Step 5: Apply Migrations
Prepare the database:
```bash
python manage.py makemigrations
python manage.py migrate
```

### Step 6: Run the Server
Start the development server:
```bash
python manage.py runserver
```
Open your browser and visit: **http://127.0.0.1:8000**

---

## How to Use the App

### 1. Chat Functionality
- Sign up or log in with your credentials.
- Once logged in, you'll see a list of other registered users.
- Select a user to start chatting in real time.
- Your chat history will be saved and displayed every time you open the conversation.

### 2. AWS Lambda Function: Add Numbers
- Visit the endpoint to add two numbers:
  ```
  http://127.0.0.1:8000/add_numbers/?num1=10&num2=20
  ```
- Replace `10` and `20` with the numbers you want to add.
- The result will be returned in JSON format (e.g., `{ "result": 30 }`).

### 3. Upload Files to S3
- Use a tool like Postman or a frontend form to upload a file:
  - URL: `http://127.0.0.1:8000/upload_to_s3/`
  - Method: POST
  - Form Data: Include the file under the key `file`.
- The file will be uploaded to your S3 bucket, and the response will include the file URL.

---

## Folder Structure
```
chat_project/
├── chat_app/
│   ├── migrations/       # Database migrations
│   ├── templates/        # HTML files
│   ├── static/           # CSS and static assets
│   ├── views.py          # Main logic for the app
│   ├── urls.py           # Routes for the app
│   ├── models.py         # Database models
│   ├── consumers.py      # WebSocket logic
├── chat_project/
│   ├── settings.py       # App settings
│   ├── urls.py           # Main app routes
│   ├── asgi.py           # For WebSockets
│   ├── wsgi.py           # For deployment
├── manage.py             # Runs the app
├── requirements.txt      # Python dependencies
└── README.md             # This file!
```

---

## Troubleshooting

### "Django not installed" Error
Make sure you've activated the virtual environment:
```bash
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### AWS Credentials Issue
Ensure your `.env` file is correctly configured with valid AWS credentials.

### WebSocket Issues
Check that you are running the app with `ASGI` configured properly (default in this project).


