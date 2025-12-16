# BizConnect Frontend

BizConnect is a comprehensive platform designed to bridge the gap between students, entrepreneurs, and investors. It fosters a collaborative ecosystem where users can connect, share opportunities, and grow together.

## 🚀 Features

### 🌟 General
- **Authentication**: Secure Login and Signup functionality using Firebase Authentication.
- **Role-Based Access**: tailored portals for Entrepreneurs, Investors, and Students.
- **Responsive Design**: Built with Tailwind CSS and DaisyUI for a seamless experience across devices.
- **Interactive UI**: Smooth animations powered by Framer Motion.

### 🏢 Entrepreneur Portal
- **Profile Management**: Manage personal and startup profiles.
- **Networking**: Find Partners, Investors, and Mentors.
- **Recruitment**: Post jobs and find employees.
- **Startup Management**: Showcase startups and track progress.

### 💼 Investor Portal
- **Discovery**: Find promising Startups to invest in.
- **Profile**: Manage investor profile and preferences.
- **Opportunities**: Browse job openings and other opportunities.

### 🎓 Student Portal
- **Career Growth**: Find Jobs and internships.
- **Guidance**: Access resources and guidance for career development.
- **Profile**: Showcase skills and academic achievements.

## 🛠️ Tech Stack

- **Frontend Framework**: [React](https://reactjs.org/) (Vite)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) & [DaisyUI](https://daisyui.com/)
- **Routing**: [React Router DOM](https://reactrouter.com/)
- **State Management & Data Fetching**: [React Query](https://tanstack.com/query/latest) & Context API
- **Authentication**: [Firebase](https://firebase.google.com/)
- **HTTP Client**: [Axios](https://axios-http.com/)
- **Animations**: [Framer Motion](https://www.framer.com/motion/)
- **Icons**: [React Icons](https://react-icons.github.io/react-icons/)

## ⚙️ Getting Started

Follow these steps to set up the project locally.

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn

### Installation

1.  **Clone the repository**
    ```bash
    git clone <repository-url>
    cd BizConnect_Frontend
    ```

2.  **Install dependencies**
    ```bash
    npm install
    ```

3.  **Configure Environment Variables**
    Create a `.env` file in the root directory and add your Firebase configuration keys:
    ```env
    VITE_apiKey=YOUR_API_KEY
    VITE_authDomain=YOUR_AUTH_DOMAIN
    VITE_projectId=YOUR_PROJECT_ID
    VITE_storageBucket=YOUR_STORAGE_BUCKET
    VITE_messagingSenderId=YOUR_MESSAGING_SENDER_ID
    VITE_appId=YOUR_APP_ID
    ```

4.  **Run the development server**
    ```bash
    npm run dev
    ```

## 📂 Project Structure

```
BizConnect_Frontend/
├── public/              # Static assets (images, JSON data)
├── src/
│   ├── assets/          # Project assets
│   ├── auth/            # Authentication provider and logic
│   ├── components/      # Reusable UI components (Sidebar, TopBar, etc.)
│   ├── firebase/        # Firebase configuration
│   ├── hooks/           # Custom React hooks (useUser, useEntrepreneur, etc.)
│   ├── pages/           # Application pages
│   │   ├── Entrepreneur/# Entrepreneur specific pages
│   │   ├── Investor/    # Investor specific pages
│   │   ├── Student/     # Student specific pages
│   │   ├── Login.jsx
│   │   ├── Signup.jsx
│   │   └── Info.jsx
│   ├── App.jsx          # Main App component
│   └── main.jsx         # Entry point and Router configuration
├── .env                 # Environment variables
├── package.json         # Project dependencies and scripts
├── tailwind.config.js   # Tailwind CSS configuration
└── vite.config.js       # Vite configuration
```
