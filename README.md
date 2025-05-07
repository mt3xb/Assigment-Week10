# Assigment-Week10
This project demonstrates how to deploy a full-stack MERN blog application on AWS using free-tier services. It includes:

- React frontend hosted on S3
- Express backend running on EC2
- MongoDB Atlas as the database
- Media uploads handled via S3
- IAM user for secure access to the media bucket

---

## 🚀 Deployment Steps

### ✅ MongoDB Atlas
- Used the existing connection string from the `.env` file:




### ✅ S3 – Frontend Bucket
- Created bucket: `m3-blogapp-frontend`
- Disabled "Block all public access"
- Enabled static website hosting
- Added a bucket policy to allow public access

### ✅ S3 – Media Bucket
- Created bucket: `m3-blogapp-media`
- Disabled "Block all public access"
- Configured CORS for browser upload support
- Tested uploading and retrieving a file

### ✅ IAM User & Policy
- Created IAM user: `blog-app-user`
- Created and attached a custom policy to access the media bucket
- Saved the access key and secret key securely (not shared)

### ✅ EC2 – Backend Setup
- Launched EC2 instance (t3.micro, Ubuntu 22.04, region: eu-north-1)
- Opened required ports: 22, 80, 443, 5000
- Ran user data script to install Node.js, PM2, and AWS CLI
- Cloned project repository
- Created `.env` files in both `backend` and `frontend` directories
- Installed dependencies and started backend using PM2

### ✅ Frontend Deployment
- Built the React app:
```bash
npm install
npm run build

    Synced the dist/ folder to the S3 frontend bucket:

    aws s3 sync dist/ s3://m3-blogapp-frontend/

✅ Success Criteria

Ability to create and edit blog posts

Ability to upload and view media files

Public access to frontend via S3

Backend running and responding on EC2

MongoDB Atlas database reachable and functional

