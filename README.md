<p align="center">
  <img src="https://raw.githubusercontent.com/explomind1/AI-Conference-Dialogue-Analyzer/main/d_C5Ju6Y8N.svg" >
</p>



# AI Conference Dialogues Analyzer

## Overview
The AI Conference Dialogue Analyzer leverages AWS technologies, including Lambda, API Gateway, and SES, to process recorded conference conversations stored in Firestore. It organizes these dialogues by group numbers retrieved from a Google Sheet, generates insightful CSV reports, and uploads them to AWS S3. The system then dynamically formats and sends these reports as professional emails using AWS SES. This setup allows for efficient analysis and sharing of conference data, facilitating better understanding and utilization of recorded dialogues for various analytical purposes.

## Features
- **Advanced Data Retrieval**: Systematically fetches and processes user inputs from a Firestore database, ensuring accurate capture and organization of data for processing.
- **Integrated Spreadsheet Management**: Leverages the Google Sheets API to dynamically organize data based on specified group numbers, facilitating the seamless handling of large datasets.
- **Robust Dynamic Reporting**: Automatically generates detailed CSV reports for designated groups, incorporating corresponding dialogues and storing them on AWS S3 for secure and scalable access.
- **Proactive Email Notifications**: Utilizes AWS SES to dynamically compose and dispatch professional email reports containing links to the CSV files, streamlining communication and data dissemination.

## Architecture
1. **AWS Lambda**: Acts as the core processing unit, orchestrating the backend logic to interact seamlessly with Firestore for data retrieval, S3 for data storage, Google Sheets for data organization, and SES for email dispatch.
2. **API Gateway**: Provides a robust interface for external triggers, allowing users to initiate data processing and specify parameters such as email recipients, enhancing user interaction and flexibility.
3. **Firestore**: Serves as the primary database, robustly storing all user dialogues and providing a reliable source for data fetching and query handling.
4. **Google Sheets**: Employs advanced API functionalities to manage and retrieve group-related data efficiently, which is crucial for organizing and processing large volumes of dialogues.
5. **AWS S3**: Manages the storage and retrieval of generated CSV reports, ensuring high availability and secure access through meticulously generated URLs.
6. **AWS SES**: Manages all aspects of email communications, from crafting to sending emails, ensuring that reports are delivered timely to the right recipients with professional formatting.

## Setup
### Prerequisites
- An active AWS account with configured access to Lambda, S3, SES, and API Gateway.
- A Firebase project with Firestore enabled for database functionalities.
- A Google Cloud project with the Sheets API enabled for handling spreadsheet-based data operations.

### Configuration
1. **Firebase Setup**:
   - Confirm that your Firebase project is properly configured and that Firestore is active.
   - Update the `config.py` file with your specific Firebase credentials to ensure secure and uninterrupted access to the database.

2. **Google Cloud Setup**:
   - Activate the Google Sheets API within your Google Cloud Console to harness its capabilities for data manipulation and retrieval.
   - Securely download the service account key and ensure it is safely uploaded to an AWS S3 bucket, setting up the foundation for API authentication and authorization.

## AWS Setup
This section provides a comprehensive guide on configuring AWS services, including AWS Lambda, API Gateway, S3, SES, and using Cloud9 for dependency management.

### Cloud9 Setup
- **Initialize your AWS Cloud9 Environment**: Start by setting up a Cloud9 environment in your AWS console. This IDE will be used to write, run, and debug the Lambda function code.
- **Install Dependencies**: Within Cloud9, you can install necessary libraries and dependencies directly into your environment which makes managing Lambda functions easier. For example, you can use the following commands to install required Python packages:
  ```bash
  pip install boto3 google-auth google-auth-oauthlib google-auth-httplib2 firebase-admin
  ```
- **Package Your Application**: After installing dependencies, package your application along with its dependencies into a deployment package. This can be done using a virtual environment or directly zipping the environment libraries.

### Lambda Function
- **Create a Lambda Function**: In the AWS Management Console, create a new Lambda function. Choose an appropriate runtime (e.g., Python 3.x), and use the execution role that has permissions to access AWS services like Firestore, S3, SES, and CloudWatch.
- **Upload Your Code**: Use AWS Cloud9 to develop and then upload your Python script directly to Lambda. Alternatively, you can zip your code and dependencies in Cloud9 and upload them manually.

### API Gateway
- **Setup API Gateway**: Create a new API Gateway to trigger your Lambda function. Define the HTTP methods that your API will support, such as GET or POST, and secure your API using API keys or IAM permissions.
- **Configure Endpoints**: Link your API Gateway to your Lambda function by creating a new trigger. Set up resource paths, query parameters, and request/response transformations as needed.

### S3 Bucket
- **Configure S3 Bucket**: Create a new S3 bucket to store the generated CSV files. Ensure that the bucket has the correct permissions to allow access from your Lambda function and restricted public access.
- **Bucket Policies and CORS**: Set up bucket policies to manage permissions and configure CORS settings if your CSV files will be accessed from web applications.

### SES Configuration
- **Verify Email Addresses**: Before sending emails through SES, verify the email addresses used in both sender and recipient fields. This is a mandatory step to comply with AWS SES policies.
- **Setup SES**: Configure your SES to manage email sending limits, and monitor your sending activity through the SES dashboard. You may also want to create a dedicated IAM user for SES activities to enhance security.

### Deployment and Testing
- **Deploy Your API**: Once your API Gateway and Lambda function are configured, deploy your API. Test it using tools like Postman or directly from your application to ensure it triggers Lambda functions correctly and handles responses.
- **Monitor and Debug**: Use AWS CloudWatch to monitor logs and troubleshoot any issues with your Lambda function or other AWS services.

## Usage
To use this system, make an API request through the configured API Gateway endpoint with the necessary query parameters (e.g., recipient email). The system will then process the data and send a detailed email to the specified address.

## Contributing
Contributions to this project are welcome. Please fork the repository, make your changes, and submit a pull request.


## Contact
For any further queries or technical support, please contact [emreturan1269@gmail.com](mailto:emreturan1269@gmail.com).

