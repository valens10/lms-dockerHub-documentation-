# Leave Management System — Docker Deployment

This project is a full Leave Management System built as part of a coding assessment. It includes:

- **Backend**: Java Spring Boot (AI-first development using Cursor)
- **Frontend + Tailwind**: Angular Lovable frontend framework
- **Authentication**: Google Login (used instead of Microsoft Authenticator due to account limitations)
- **Dockerized setup** for seamless deployment and testing

---

## 🐳 Docker Setup Instructions

### 📁 Project Structure

```
leave-management-docker/
│
├── .env.example/                 # Environment variables examples
├── .env                          # Environment variables file
├── docker-compose.yml            # Docker configuration
└── README.md                     # This documentation
```

### 📁 Requirements

- Docker installed on your system
- `.env` file with necessary environment variables (see below)

### Project Setup
1. Clone repostory `https://github.com/valens10/lms-dockerHub-documentation-.git`
2. cd `lms-dockerHub-documentation`

### 💠 Environment Variables (`.env`)

Create a `.env` file in the root of your project and include the following variables:

```env
POSTGRES_DB=leave_db
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_postgres_password
POSTGRES_URL=jdbc:postgresql://postgres:5432

JWT_SECRET=your_jwt_secret
JWT_EXPIRATION=3600000

SENDGRID_API_KEY=your_sendgrid_api_key
SENDGRID_FROM_EMAIL=your_email@example.com

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_REDIRECT_URI=http://localhost:8080/oauth2/callback/google

FRONTEND_URL=http://localhost:4200
API_URL=http://localhost:8080
```

---

## 🚀 Running the App

From the root of your project directory, run the following:

```bash
docker compose up -d
```

This will spin up:

- **PostgreSQL** on port `5432`
- **Backend API** on port `8080`
- **Frontend** on port `4200`

## 🧪 Accessing the Application

- **Frontend**: [http://localhost:4200](http://localhost:4200)
- **Backend API**: [http://localhost:8080](http://localhost:8080)
- **Swagger API Docs**: [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

---

## 🧪 Health Check & Troubleshooting

- PostgreSQL uses `pg_isready` for health checks.
- The Spring Boot backend is health-checked at: `http://localhost:8080/actuator/health`

You can check container statuses with:

```bash
docker ps -a
```

To remove stopped containers:

```bash
docker container prune
```

---

## 🗃 Repositories

- **Backend**: [https://github.com/valens10/jst_leave_management_api.git](https://github.com/valens10/jst_leave_management_api.git)
- **Frontend**: [https://github.com/valens10/lms-fronted.git](https://github.com/valens10/lms-fronted.git)

---

## 🧠 AI-First Development Note

This project was built using **Cursor IDE**  and **ChatGpt**  with AI pair programming to boost development efficiency and ensure a production-ready codebase within a short timeframe.

---

## 🔒 Authentication Note

- Due to temporary Microsoft Authenticator access limitations, Google Authentication was implemented with full OAuth2 integration. You can test login flows using any Gmail account.

- The first `Google-authenticated user` will automatically be assigned `Admin privileges` in the system and
subsequent users will be assigned roles according to the regular logic (e.g., staff or manager, and Admin).

---

## 📦 Docker Hub Images

- **Backend Image**: `valens10/leave-management-backend:latest`
- **Frontend Image**: `valens10/leave-management-frontend:latest`

---

## 🚼 Cleanup

To stop and clean up:

```bash
docker compose down -v
```

This will stop all containers and remove associated volumes.

---

---

## 🧪 Testing All Functionalities

📸 **(Screenshots Section)**

✅ **Step-by-step Testing Checklist**:

### 1. Api Documentation
- [] Swagger Docs
![image](https://github.com/user-attachments/assets/b7b72333-d990-40b3-8b78-bd037c324617)

### 1. Authentication
- [ ] Login using Google account
![image](https://github.com/user-attachments/assets/0fa63097-11eb-40f8-9aa3-b9d6078576f3)

- [ ] Avatar (Google profile picture) is loaded


### 2. Dashboard
- [ ] View current leave balance
- [ ] Display upcoming holidays
![image](https://github.com/user-attachments/assets/f2167ea5-3e20-44d7-a789-b31c3e7447b1)

### 3. Leave Application
- [ ] Select leave type
- [ ] Apply for full-day / half-day
- [ ] Attach document (medical, etc.)
- [ ] Submit and track status
![image](https://github.com/user-attachments/assets/df5029d9-2239-4667-b5ee-bdab1c76b66f)

### 4. Approval Workflow
- [ ] Approver receives notification
- [ ] Stafs receives notification when their leaves approved/rejected
- [ ] Approver can approve/reject with comment

![image](https://github.com/user-attachments/assets/2a60235a-dfff-42a6-8a42-1ed8cf1d67db)
![image](https://github.com/user-attachments/assets/924ec721-94c2-481c-9717-01ceb25ea2f1)


### 5. Leave Balance Management (cron job schedules using spring boot schedule)
- [ ] Check auto-accrual calculation
- [ ] Carry forward up to 5 days
- [ ] Admin makes manual adjustment
![image](https://github.com/user-attachments/assets/afad5e54-0256-4750-a9a1-7378f327392f)
![image](https://github.com/user-attachments/assets/54008bd5-b28c-400e-aacf-9d5e575ea7ab)
![image](https://github.com/user-attachments/assets/66fb2cee-f61d-429f-b86a-0362d4fd0c39)


### 6. Admin Panel
- [ ] Manage leave types
- [ ] Manager Department
- [ ] View department calendars
- [ ] Generate reports (Excel)
![image](https://github.com/user-attachments/assets/bc399484-93ac-41b7-8a57-fd92e27ec436)
![image](https://github.com/user-attachments/assets/49b7f278-681a-4b42-9d47-22044c1d15c4)
![image](https://github.com/user-attachments/assets/d93c8bf5-036a-4e6f-bd9a-78f7accf31b9)
![image](https://github.com/user-attachments/assets/6084b7f5-20d0-4aad-bc77-7fc3695106a5)


### 2. Staff Dashboard
![image](https://github.com/user-attachments/assets/4aee725a-09fd-4125-963e-ab5bcb10ed65)
![image](https://github.com/user-attachments/assets/8905e2af-a516-47a3-b3da-e7808ad7af81)



### 7. Notifications
- [ ] Email and/or in-app alerts on all leave lifecycle events

### 8. Permissions & Roles
- [ ] Role-based access verified (Staff, Manager, Admin)

---

## 💬 Feedback

Feel free to reach out with any questions or suggestions. Thank you for the opportunity!

