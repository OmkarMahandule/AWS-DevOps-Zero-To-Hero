## Creating an IAM User in AWS (Step-by-Step)

### 1. Login to AWS Console
- Open AWS Management Console
- Sign in using your **root** account

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/f1eef752-27b2-40a9-b3cf-7899a0f7f794" />


### 2. Open IAM Dashboard
- Search for **IAM** in the AWS search bar
- Click **IAM (Identity and Access Management)**

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/f4362982-e02b-4605-8b36-435fdd234227" />


### 3. Set User Details
- Enter a **username**
- Select access type:
  -  AWS Management Console access
  -  Programmatic access (CLI/API)
    
    <img width="800" height="609" alt="image" src="https://github.com/user-attachments/assets/f31e21eb-91b1-4982-a57c-7ada09257f49" />

### 4. Assign Permissions
Choose one method:

- Add user to group (recommended)
- Attach policies directly
- Example policies:
  - `AdministratorAccess`
  - `AmazonS3ReadOnlyAccess`
  - `EC2FullAccess`


  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/6ea36cdb-b465-43d6-a74a-7021b2a27489" />

### 5. Finish Setup

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/3fa2e29c-1cc8-434b-9832-b3d434cfda2c" />


---
