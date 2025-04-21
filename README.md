# Leave Management System — Docker Deployment

This project is a full Leave Management System built as part of a coding assessment. It includes:

- **Backend**: Java Spring Boot (AI-first development using Cursor)
- **Frontend**: Angular Lovable frontend framework
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
_Add relevant screenshots of each tested functionality here before submission._

✅ **Step-by-step Testing Checklist**:

### 1. Api Documentation
- [] Swagger Docs

### 1. Authentication
- [ ] Login using Google account
- [ ] Avatar (Google profile picture) is loaded

### 2. Dashboard
- [ ] View current leave balance
- [ ] Display upcoming holidays
- [ ] Display teammates currently on leave

### 3. Leave Application
- [ ] Select leave type
- [ ] Apply for full-day / half-day
- [ ] Attach document (medical, etc.)
- [ ] Submit and track status

### 4. Approval Workflow
- [ ] Approver receives notification
- [ ] Stafs receives notification when their leaves approved/rejected
- [ ] Approver can approve/reject with comment

### 5. Leave Balance Management (cron job schedules)
- [ ] Check auto-accrual calculation
- [ ] Carry forward up to 5 days
- [ ] Admin makes manual adjustment

### 6. Admin Panel
- [ ] Manage leave types
- [ ] Manager Department
- [ ] View department calendars
- [ ] Generate reports (Excel)

### 7. Notifications
- [ ] Email and/or in-app alerts on all leave lifecycle events

### 8. Permissions & Roles
- [ ] Role-based access verified (Staff, Manager, Admin)

---

## 💬 Feedback

Feel free to reach out with any questions or suggestions. Thank you for the opportunity!

