# Project Report: AWS S3 Flask Uploader

## **Sourabh Narnaulia | 6/01/25 | Building a Secure Image Storage and Sharing Application Using AWS** | **AWS

## Git link: https://github.com/srbhcodes/AWS-S3-Flask-Uploader

### **Scope of Project**
The purpose of this project is to build a web application that allows users to upload files directly to an AWS S3 bucket. The application should streamline file management and demonstrate the integration of AWS S3 with a Flask backend, ensuring secure and efficient handling of file uploads.

### **Technologies Used**
- **Backend**: Flask (Python)
- **Cloud Storage**: Amazon S3
- **Frontend**: HTML, CSS, JavaScript
- **Development Tools**: Git, GitHub, Nano/VSCode
- **Environment Variables Management**: Python `os` module for handling secrets securely

### **Steps Taken**
1. **Initialize the Project**: 
   - Set up a new Git repository for version control.
   - Create the basic structure for the Flask project.

2. **AWS S3 Setup**:
   - Configure an S3 bucket with appropriate permissions for file uploads.
   - Generate an AWS Access Key ID and Secret Access Key for integration.

3. **Flask Application Development**:
   - Write Flask routes to handle file uploads and return responses.
   - Implement logic to securely upload files from the application to the S3 bucket.

4. **Secure Sensitive Information**:
   - Store AWS credentials in environment variables or a `.env` file.
   - Ensure that secrets are excluded from version control by using `.gitignore`.

5. **Test the Application**:
   - Upload test files to validate the integration with AWS S3.
   - Handle edge cases such as large files and invalid inputs.

6. **Remove Credentials from Git History**:
   - Rebase Git history to remove sensitive information from past commits.
   - Push clean code to the GitHub repository with updated commit history.

7. **Finalize and Push Code**:
   - Reinitialize the Git repository to remove history with sensitive data.
   - Create an initial commit and push to GitHub with proper repository rules in place.

### **Project Outcome**
The project successfully integrates a Flask backend with AWS S3, enabling users to upload files securely and efficiently. Sensitive AWS credentials have been removed from version control, ensuring the project's compliance with best practices. The completed application is ready for deployment and further enhancement.

---

### Screenshots

Server running:
![[Pasted image 20250107204520.png]]

Uploded Images to S3 bucket:
![[Pasted image 20250107205034.png]]