<div align="center">

<img src="public/logo/BizConnect.png" alt="BizConnect logo" width="260" />

# BizConnect

**One platform where entrepreneurs, investors and students find each other.**

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=61DAFB&labelColor=0A0A12)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=646CFF&labelColor=0A0A12)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38BDF8?style=for-the-badge&logo=tailwindcss&logoColor=38BDF8&labelColor=0A0A12)](https://tailwindcss.com/)
[![DaisyUI](https://img.shields.io/badge/DaisyUI-4-5A0EF8?style=for-the-badge&logo=daisyui&logoColor=5A0EF8&labelColor=0A0A12)](https://daisyui.com/)
[![Firebase Auth](https://img.shields.io/badge/Firebase-Auth-FFCA28?style=for-the-badge&logo=firebase&logoColor=FFCA28&labelColor=0A0A12)](https://firebase.google.com/)
[![React Router](https://img.shields.io/badge/React_Router-6-CA4245?style=for-the-badge&logo=reactrouter&logoColor=CA4245&labelColor=0A0A12)](https://reactrouter.com/)
[![React Query](https://img.shields.io/badge/React_Query-3-FF4154?style=for-the-badge&logo=reactquery&logoColor=FF4154&labelColor=0A0A12)](https://tanstack.com/query/v3)
[![Axios](https://img.shields.io/badge/Axios-1-5A29E4?style=for-the-badge&logo=axios&logoColor=5A29E4&labelColor=0A0A12)](https://axios-http.com/)
[![Framer Motion](https://img.shields.io/badge/Framer_Motion-11-0055FF?style=for-the-badge&logo=framer&logoColor=white&labelColor=0A0A12)](https://www.framer.com/motion/)

</div>

---

## Overview

Early-stage founders struggle to find co-founders, funding, mentors and hires. Investors want a filtered view of startups that are actually raising. Students want jobs and a clear idea of what to learn next. These groups rarely meet in one place.

BizConnect is the React frontend for a role-based networking platform that puts all three groups in a single app. Each user signs up with a role, completes a role-specific profile, and lands in a portal built around what that role needs.

## Features

### General

- Email and password sign up and login with **Firebase Authentication**
- Role chosen at sign up (Entrepreneur, Investor, Student) and resolved from the API at login
- First-time users are routed to a role-specific onboarding form (`/info/:role`); returning users go straight to their portal
- Shared portal layout: top bar with "Edit Info" and logout, plus a responsive sidebar drawer on mobile
- Animated landing page built with Framer Motion
- Toast notifications via `react-hot-toast`; multi-select skill and interest pickers via `react-select`

### Entrepreneur

| Feature | What it does |
| --- | --- |
| Profile | View industry, job title, skills, interests, experience, funds raised and partnership status |
| Startups | Add a startup (name, description, industry, funding raised, goal, current funding, fundraising status) and list your own startups |
| Jobs | Post a job (title, description, requirements, skills, company, deadline), list your postings and delete them |
| Find Co-founders | Browse potential partners, filter by skill and interest |
| Find Investors | Browse investors, filter by skill and interest, view details, contact by email |
| Find Mentors | Browse mentors, filter by skill and interest |
| Find Employees | Browse student profiles to hire from |

### Investor

| Feature | What it does |
| --- | --- |
| Profile | View interests, skills, experience, total investments, companies, and openness to investing or mentoring |
| Find Startups | Browse startups that are raising, filter by industry, contact the founder |
| Post Jobs | Post and manage job listings (shared Jobs page) |

### Student

| Feature | What it does |
| --- | --- |
| Profile | View major, graduation year, skills, interests, education and employment status |
| Find Jobs | Browse posted jobs, open details, contact the poster by email |
| AI Guide | Requests personalized suggested skills, courses, career path, career roadmap and skills roadmap from the backend, caches the result locally, and can regenerate on demand |

## How it fits together

```mermaid
flowchart TD
    L[Landing /] --> S[Sign up<br/>choose role]
    L --> LG[Login]
    S --> I["Onboarding /info/:role"]
    LG -->|no profile yet| I
    LG -->|profile exists| R{Role}
    I --> R

    R -->|entrepreneur| E[Entrepreneur Portal]
    R -->|investor| V[Investor Portal]
    R -->|student| ST[Student Portal]

    E --> E1[Profile] & E2[Startups] & E3[Jobs] & E4[Find Co-founders] & E5[Find Investors] & E6[Find Mentors] & E7[Find Employees]
    V --> V1[Profile] & V2[Find Startups] & V3[Post Jobs]
    ST --> S1[Profile] & S2[Find Jobs] & S3[AI Guide]

    subgraph Services
        FB[(Firebase Auth)]
        API[(REST API<br/>localhost:3000)]
    end

    S -.-> FB
    LG -.-> FB
    LG -.-> API
    I -.-> API
    E2 & E3 & E5 & V2 & S2 & S3 -.-> API
```

## Tech Stack

| Layer | Tools |
| --- | --- |
| UI | React 18, Vite 5 |
| Styling | Tailwind CSS 3, DaisyUI 4 |
| Routing | React Router DOM 6 (`createBrowserRouter`) |
| Server state | React Query 3 |
| App state | React Context (`AuthProvider`) |
| Auth | Firebase Authentication (email and password) |
| HTTP | Axios (shared instance in `useAxiosPublic`) |
| UX | Framer Motion, react-hot-toast, react-select, React Icons |
| Tooling | ESLint, PostCSS, Autoprefixer |

## Routes

| Path | Page | Access |
| --- | --- | --- |
| `/` | Landing page | Public |
| `/login` | Login | Public |
| `/signup` | Sign up with role | Public |
| `/info/:role` | Role-specific onboarding and edit info | Signed in |
| `/entrepreneur`, `/entrepreneur/profile` | Entrepreneur profile | Entrepreneur |
| `/entrepreneur/startups` | Add and list startups | Entrepreneur |
| `/entrepreneur/jobs` | Post and manage jobs | Entrepreneur |
| `/entrepreneur/findPartners` | Find co-founders | Entrepreneur |
| `/entrepreneur/findInvestors` | Find investors | Entrepreneur |
| `/entrepreneur/findMentors` | Find mentors | Entrepreneur |
| `/entrepreneur/findEmployees` | Find employees | Entrepreneur |
| `/investor`, `/investor/profile` | Investor profile | Investor |
| `/investor/findStartups` | Find startups | Investor |
| `/investor/jobs` | Post and manage jobs | Investor |
| `/student`, `/student/profile` | Student profile | Student |
| `/student/findJobs` | Find jobs | Student |
| `/student/guidence` | AI Guide | Student |

> The "Access" column reflects which portal links to each route. Routes are not guarded in the router itself.

## Project Structure

```
BizConnect-frontend/
├── public/
│   ├── Home/              # Landing page imagery
│   ├── logo/              # BizConnect logo
│   ├── topBarJson/        # Sample JSON data
│   └── *.json             # Sample data (startups, jobs, investors, students, ...)
├── src/
│   ├── assets/            # Avatar SVGs used by ProfilePicture
│   ├── auth/
│   │   └── AuthProvider.jsx        # Firebase auth context
│   ├── components/
│   │   ├── ProfilePicture.jsx
│   │   ├── Sidebar.jsx             # Role-aware navigation drawer
│   │   └── TopBar.jsx              # Greeting, edit info, logout
│   ├── firebase/
│   │   └── firebase.config.js      # Firebase init from env vars
│   ├── hooks/
│   │   ├── useAxiosPublic.jsx      # Axios instance (base URL)
│   │   ├── useEntrepreneur.jsx
│   │   ├── useInvestor.jsx
│   │   ├── useRole.jsx
│   │   ├── useStudent.jsx
│   │   └── useUser.jsx
│   ├── pages/
│   │   ├── Entrepreneur/   # Portal, Profile, Startups, Jobs, Find*
│   │   ├── Investor/       # Portal, Profile, FindStartups, FindMentees
│   │   ├── Student/        # Portal, Profile, FindJobs, Guide
│   │   ├── Info.jsx        # Role-specific onboarding form
│   │   ├── Login.jsx
│   │   └── Signup.jsx
│   ├── App.jsx             # Landing page
│   └── main.jsx            # Router, QueryClient and AuthProvider setup
├── index.html
├── tailwind.config.js
├── postcss.config.js
└── vite.config.js
```

## Getting Started

### Prerequisites

- Node.js and npm
- A Firebase project with Email/Password sign-in enabled
- The BizConnect backend API running on `http://localhost:3000` (base URL set in `src/hooks/useAxiosPublic.jsx`)

### Install and run

```bash
git clone https://github.com/Tanvir-Chowdhury/BizConnect-frontend.git
cd BizConnect-frontend
npm install
npm run dev
```

### Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite dev server |
| `npm run build` | Build for production into `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint on `.js` and `.jsx` files |

## Environment Variables

Create a `.env` file in the project root with your Firebase web app config. These are read in `src/firebase/firebase.config.js`.

| Variable | Purpose |
| --- | --- |
| `VITE_apiKey` | Firebase API key |
| `VITE_authDomain` | Firebase auth domain |
| `VITE_projectId` | Firebase project ID |
| `VITE_storageBucket` | Firebase storage bucket |
| `VITE_messagingSenderId` | Firebase messaging sender ID |
| `VITE_appId` | Firebase app ID |

## Author

**Md Tanvir Chowdhury**

[![GitHub](https://img.shields.io/badge/GitHub-Tanvir--Chowdhury-181717?style=for-the-badge&logo=github&logoColor=white&labelColor=0A0A12)](https://github.com/Tanvir-Chowdhury)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-8B24DD?style=for-the-badge&logo=googlechrome&logoColor=white&labelColor=0A0A12)](https://tanvir-chowdhury.github.io/tanvir-portfolio/)
