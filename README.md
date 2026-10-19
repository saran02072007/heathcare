# Online MediConnect Medicare 🩺

> A modern, responsive full-stack digital healthcare management web application enabling patients to find certified physicians, schedule appointments online with real-time double-booking prevention, receive digital prescriptions, and manage healthcare records seamlessly.

---

## 🌟 Key Features

### 1. Patient Portal
- **Doctor Directory & Filtering**: Search and filter doctors by medical specialty, location, availability days, ratings, and consultation fees.
- **Appointment Scheduling**:
  - Interactive calendar date and slot selector.
  - Choice between **Online Video Telehealth** and **In-Person Clinic Visit**.
  - **Automated Double-Booking Protection**: Prevents conflicting bookings for the same doctor and time slot.
  - Unique appointment reference code generation (e.g. `MCM-2026-8921`).
  - Confetti celebration upon confirmed booking.
- **Patient Dashboard**:
  - Upcoming appointments with direct telehealth meeting link or clinic address.
  - Consultation history with full status tracking (`Confirmed`, `Pending`, `Completed`, `Cancelled`).
  - Self-service appointment cancellation with instant slot release.
  - **Digital Prescriptions**: View and print doctor prescriptions with diagnosis, medication tables, lab recommendations, and physician digital signature.
  - Personal health profile: track blood group, known drug/food allergies, chronic conditions, and emergency contacts.

### 2. Doctor Portal
- **Consultation Schedule Management**: Set available days, time slots, consultation fees ($), and hospital location.
- **Appointment Queue**: Real-time view of daily and upcoming patient appointments.
- **Status Updates**: Confirm pending appointments, conduct consultations, and mark as completed or cancelled.
- **Prescription Creator**: Prescribe medications (name, dosage, frequency, duration, instructions), order diagnostic tests, and attach advice directly into the patient's record.

### 3. Administrator Dashboard
- **Executive Analytics**: Total registered patients, doctors, appointments, pending requests, and gross revenue.
- **Visual Analytics**: Monthly consultation trends and distribution of doctors across medical specialties.
- **Master Appointments Directory**: Filter, search, and update any appointment across the hospital system.
- **User Account Management**: View all patients and doctors, with one-click account activation / deactivation.
- **Inquiry & Support Desk**: Review contact form submissions and toggle status (`Unread`, `Read`, `Replied`).

### 4. 1-Click Instant Demo Persona Switcher
A persistent dropdown in the navigation bar lets evaluators and professors test all three roles with zero typing:
- **Patient**: `patient.john@example.com` / `patient123`
- **Doctor**: `doctor.sarah@mediconnect.com` / `doctor123`
- **Admin**: `admin@mediconnect.com` / `admin123`

---

## 💻 Technology Stack

| Layer | Technologies |
| :--- | :--- |
| **Frontend** | React 19, Vite, Tailwind CSS, Lucide React, React Router DOM, Canvas-Confetti |
| **Backend** | Node.js, Express.js (ES Modules) |
| **Database** | MongoDB & Mongoose (with built-in resilient local data store fallback) |
| **Authentication** | JSON Web Tokens (JWT), Bcrypt.js password hashing |
| **Design** | Clean medical aesthetic (white background with blue, teal, and emerald accents) |

---

## 📁 Project Architecture

```
LAK1/
├── backend/
│   ├── config/
│   │   └── db.js                 # MongoDB connection with graceful local store fallback
│   ├── controllers/
│   │   ├── adminController.js       # Analytics, user management, and stats
│   │   ├── appointmentController.js # Booking & double-booking prevention logic
│   │   ├── authController.js        # Register, login, me, and profile updates
│   │   ├── contactController.js     # Contact inquiries management
│   │   ├── doctorController.js      # Doctor directory, search, & schedule updates
│   │   └── prescriptionController.js# Prescription authoring & patient retrieval
│   ├── data/
│   │   ├── seedData.js              # Comprehensive clinical seed data
│   │   └── store.js                 # Unified Data Store (MongoDB + persistent local DB)
│   ├── middleware/
│   │   ├── authMiddleware.js        # JWT verification & role authorization
│   │   └── errorHandler.js          # Central API error handler
│   ├── models/
│   │   ├── Appointment.js           # Mongoose Appointment Schema
│   │   ├── ContactMessage.js        # Mongoose Contact Message Schema
│   │   ├── Doctor.js                # Mongoose Doctor Schema
│   │   ├── Prescription.js          # Mongoose Prescription Schema
│   │   └── User.js                  # Mongoose User Schema
│   ├── routes/                      # Express route definitions
│   ├── .env                         # Backend environment variables
│   ├── .env.example                 # Example configuration
│   ├── package.json
│   └── server.js                    # Express app entry point (Port 5000)
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── AppointmentModal.jsx     # Booking modal with date/time picker & confetti
│   │   │   ├── DoctorCard.jsx           # Physician directory card
│   │   │   ├── DoctorProfileModal.jsx   # Detailed physician credentials & biography
│   │   │   ├── Footer.jsx               # Medical footer with 24/7 hotline & emergency info
│   │   │   ├── Navbar.jsx               # Responsive nav with 1-click demo switcher
│   │   │   ├── PrescriptionModal.jsx    # Printable official prescription slip
│   │   │   └── ProtectedRoute.jsx       # Role-based route guard
│   │   ├── context/
│   │   │   └── AuthContext.jsx          # Authentication state & quick demo logins
│   │   ├── pages/
│   │   │   ├── About.jsx                # Mission, vision, & digital healthcare benefits
│   │   │   ├── AdminDashboard.jsx       # Super Admin control center & analytics charts
│   │   │   ├── BookAppointment.jsx      # Dedicated booking workflow
│   │   │   ├── Contact.jsx              # Contact form & FAQ accordion
│   │   │   ├── DoctorDashboard.jsx      # Physician dashboard & prescription creator
│   │   │   ├── FindDoctors.jsx          # Searchable doctor directory with filters
│   │   │   ├── Home.jsx                 # Landing page with hero, services, testimonials
│   │   │   ├── Login.jsx                # Secure login with demo buttons
│   │   │   ├── NotFound.jsx             # 404 page
│   │   │   ├── PatientDashboard.jsx     # Patient health records & appointments
│   │   │   ├── Register.jsx             # New patient/doctor registration
│   │   │   └── Services.jsx             # 8 dedicated healthcare specialty cards
│   │   ├── services/
│   │   │   └── api.js                   # Unified API client
│   │   ├── App.jsx                      # Client router & page composition
│   │   ├── index.css                    # Tailwind CSS & healthcare aesthetic theme
│   │   └── main.jsx
│   ├── index.html                       # HTML5 metadata & Google Fonts
│   ├── package.json
│   └── vite.config.js                   # Vite config with Tailwind & proxy
├── package.json                         # Root runner scripts
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** (v18.0.0 or higher recommended)
- **npm** (v9.0.0 or higher)
- *(Optional)* **MongoDB** (If MongoDB is running, the app automatically connects to `mongodb://127.0.0.1:27017/mediconnect`. If not running, the app automatically runs in local development store mode with zero configuration needed!)

### 1. Installation

From the root directory:
```bash
# Install root dependencies
npm install

# Install backend dependencies
npm --prefix backend install

# Install frontend dependencies
npm --prefix frontend install
```

Or run all installs in one command:
```bash
npm run install:all
```

---

### 2. Environment Variables

A default `.env` is configured in `backend/.env`:
```env
PORT=5000
NODE_ENV=development
MONGO_URI=mongodb://127.0.0.1:27017/mediconnect
JWT_SECRET=mediconnect_super_secret_jwt_key_2026_healthcare_secure
FRONTEND_URL=http://localhost:5173
```

---

### 3. Running the Application

You can launch both the frontend and backend servers together or independently:

#### Option A: Run Concurrently (Recommended)
```bash
npm run dev
```

#### Option B: Run Individually

**Start Backend Server:**
```bash
cd backend
npm run dev
# Server runs on http://localhost:5000
```

**Start Frontend Application:**
```bash
cd frontend
npm run dev
# Vite runs on http://localhost:5173 (or 5174 if 5173 is occupied)
```

---

## 🔑 Pre-Seeded Demo Accounts

Use the **"Demo Accounts"** dropdown in the top navigation bar for 1-click instant login, or use these credentials:

| Role | Name | Email | Password | Access Rights |
| :--- | :--- | :--- | :--- | :--- |
| **Patient** | John Doe | `patient.john@example.com` | `patient123` | Patient Portal, Bookings, Prescriptions, Health Profile |
| **Patient 2**| Sarah Miller | `patient.sarah@example.com` | `patient123` | Patient Portal |
| **Doctor** | Dr. Sarah Jenkins | `doctor.sarah@mediconnect.com` | `doctor123` | Doctor Portal, Patient Queue, Prescription Creator, Schedule |
| **Doctor 2** | Dr. Marcus Thorne | `doctor.marcus@mediconnect.com` | `doctor123` | Doctor Portal, Dermatology Schedule |
| **Doctor 3** | Dr. Elena Rostova | `doctor.elena@mediconnect.com` | `doctor123` | Doctor Portal, Pediatrics Schedule |
| **Admin** | Dr. Eleanor Vance | `admin@mediconnect.com` | `admin123` | Admin Master Dashboard, Analytics, User Management |

---

## 📡 REST API Reference

### Authentication (`/api/auth`)
- `POST /api/auth/register` - Create new patient or doctor account
- `POST /api/auth/login` - Authenticate user & receive JWT token
- `GET /api/auth/me` - Retrieve authenticated user profile (Protected)
- `PUT /api/auth/profile` - Update patient profile, allergies, and vitals (Protected)

### Doctors (`/api/doctors`)
- `GET /api/doctors` - Query doctors with filters (`search`, `specialty`, `location`, `maxFee`, `minRating`, `day`)
- `GET /api/doctors/specialties` - List distinct specialties and doctor counts
- `GET /api/doctors/:id` - Get doctor profile and available slots
- `PUT /api/doctors/:id` - Update doctor schedule, fee, and location (Doctor / Admin)

### Appointments (`/api/appointments`)
- `POST /api/appointments` - Book appointment (Includes double-booking validation)
- `GET /api/appointments` - Get appointments for current user (Filtered by role)
- `GET /api/appointments/:id` - Get appointment details (Authorized users only)
- `PATCH /api/appointments/:id/status` - Update status to Confirmed / Completed (Doctor / Admin)
- `PATCH /api/appointments/:id/cancel` - Cancel appointment with reason

### Prescriptions (`/api/prescriptions`)
- `POST /api/prescriptions` - Issue new digital prescription (Doctor only)
- `GET /api/prescriptions` - Retrieve patient prescriptions

### Admin (`/api/admin`)
- `GET /api/admin/stats` - Platform metrics, monthly trends, and specialty distribution
- `GET /api/admin/users` - Master list of registered users with role and search filters
- `PATCH /api/admin/users/:id/toggle-status` - Activate or deactivate user accounts

### Contact (`/api/contact`)
- `POST /api/contact` - Submit support / inquiry message
- `GET /api/contact` - List submitted inquiries (Admin only)
- `PATCH /api/contact/:id/status` - Update inquiry status (Admin only)

---

## 🔒 Security & Privacy Practices
- **Password Protection**: Passwords hashed using `bcryptjs` with 10 salt rounds.
- **Route Authorization**: Strict role-based middleware (`protect` and `authorize`).
- **Data Protection**: Patient health records and prescriptions are restricted strictly to the patient, the attending physician, and system administrators.
- **Input Validation**: Server-side and client-side validation on all forms.
- **Environment Isolation**: Secrets stored in `.env`.

---

## 📄 Demonstration Disclaimer
*Online MediConnect Medicare is a digital demonstration and educational prototype created for college project presentation and portfolio evaluation. It does not provide emergency medical advice. In a real medical emergency, call 911 immediately.*
