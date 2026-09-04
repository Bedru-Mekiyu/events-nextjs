# DevEvents — Developer Event Discovery & Management Platform

[![CI Workflow](https://github.com/Bedru-Mekiyu/events-nextjs/actions/workflows/ci.yml/badge.svg)](https://github.com/Bedru-Mekiyu/events-nextjs/actions)
![Next.js](https://img.shields.io/badge/Next.js-16.0.0-black?logo=next.js)
![React](https://img.shields.io/badge/React-19.2.0-61DAFB?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38BDF8?logo=tailwindcss)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb)

**DevEvents** is a full-stack web application for discovering, managing, and showcasing developer conferences, hackathons, and meetups. Built with Next.js 16 App Router, React 19, TypeScript, Tailwind CSS, MongoDB, Cloudinary, and PostHog.

---

## 🚀 Key Features

- **Event Showcase**: Browse featured upcoming developer events on a responsive landing page with interactive canvas background effects.
- **Detailed Event Pages**: View event overviews, schedules/agendas, venue details, formats (online, offline, hybrid), audience target, tags, and organizer details.
- **Similar Event Recommendations**: Discover related events based on matching technology tags.
- **Event Booking / Registration**: Server actions to register user interest/bookings for events.
- **Media Uploads via Cloudinary**: Seamless upload and hosting for event banner images.
- **RESTful API Routes**: Comprehensive API endpoints (`/api/events`, `/api/events/[slug]`) supporting CRUD operations.
- **Next.js 16 Caching**: Leverages Next.js 16 `use cache` directive and cache life policies (`cacheLife('hours')`) for optimized page performance.
- **Product Analytics**: PostHog integration for tracking user engagement and page analytics.

---

## 🛠️ Technology Stack

- **Framework**: Next.js 16 (App Router, Turbopack, Cache Components)
- **Frontend Library**: React 19
- **Language**: TypeScript
- **Styling**: Tailwind CSS v4, OGL (3D canvas light ray effects), Lucide React icons
- **Database**: MongoDB with Mongoose ODM
- **Media Storage**: Cloudinary SDK
- **Analytics**: PostHog (`posthog-js`, `posthog-node`)
- **CI/CD**: GitHub Actions

---

## 📂 Project Structure

```text
events-nextjs/
├── .github/
│   └── workflows/
│       └── ci.yml             # GitHub Actions CI workflow (lint & build)
├── app/
│   ├── api/
│   │   └── events/            # Next.js API endpoints (GET, POST, GET [slug])
│   ├── events/
│   │   └── [slug]/            # Dynamic route for event details page
│   ├── favicon.ico
│   ├── globals.css            # Tailwind CSS and layout styling
│   ├── layout.tsx             # Root layout with Navbar, LightRays, & analytics
│   └── page.tsx               # Landing page with featured events list
├── components/                # Modular React UI components
│   ├── BookEvent.tsx          # Event booking server action form
│   ├── EventCard.tsx          # Card component for event previews
│   ├── EventDetails.tsx       # Event detail layout component
│   ├── ExploreBtn.tsx        # Scroll-to-explore CTA button
│   ├── LightRays.tsx          # Interactive WebGL canvas background component
│   └── Navbar.tsx             # Application navigation bar
├── database/                  # Mongoose schemas and database models
│   ├── booking.model.ts       # Booking schema definition
│   ├── event.model.ts         # Event schema definition & slug pre-save hook
│   └── index.ts               # Database models export entry point
├── lib/
│   ├── actions/               # Next.js Server Actions
│   │   ├── booking.actions.ts # Action to record event bookings
│   │   └── event.actions.ts   # Action to query similar events
│   ├── constants.ts
│   └── mongodb.ts             # Cached Mongoose connection helper
├── public/                    # Static assets (images, icons, logos)
├── eslint.config.mjs          # Flat ESLint configuration
├── next.config.ts             # Next.js configuration (Turbopack, cache components)
├── package.json
└── tsconfig.json
```

---

## ⚙️ Environment Variables

Create a `.env.local` file in the root directory and configure the following environment variables:

```env
# Server & API Configuration
NEXT_PUBLIC_BASE_URL=http://localhost:3000

# Database Configuration
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/devevents?retryWrites=true&w=majority

# Cloudinary Storage Configuration
CLOUDINARY_URL=cloudinary://<api_key>:<api_secret>@<cloud_name>

# PostHog Analytics
NEXT_PUBLIC_POSTHOG_KEY=phc_your_posthog_public_key
NEXT_PUBLIC_POSTHOG_HOST=https://eu.i.posthog.com
```

---

## 💻 Getting Started

### Prerequisites

Ensure you have the following installed on your local machine:
- **Node.js**: v20 or higher
- **npm**: v10 or higher

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Bedru-Mekiyu/events-nextjs.git
   cd events-nextjs
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Run the development server**:
   ```bash
   npm run dev
   ```

4. **Open application**:
   Navigate to [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📡 API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/events` | Fetches a list of all events sorted by creation date |
| `POST` | `/api/events` | Creates a new event with image upload to Cloudinary |
| `GET` | `/api/events/[slug]` | Fetches detailed information for a specific event by slug |

---

## 🧪 Quality Assurance & Building

### Linting

Run ESLint to check for code quality and syntax issues:
```bash
npm run lint
```

### Production Build

Compile and build the Next.js application for production:
```bash
npm run build
```

---

## 🔄 CI/CD Pipeline

Automated checks run via GitHub Actions on every push or pull request to the `main` branch. The CI workflow (`.github/workflows/ci.yml`) executes the following steps:
1. Environment setup (Node.js 20 & dependency caching)
2. Dependency installation (`npm ci`)
3. Static linting analysis (`npm run lint`)
4. Production build compilation (`npm run build`)

---

## 📄 License

Distributed under the MIT License.
