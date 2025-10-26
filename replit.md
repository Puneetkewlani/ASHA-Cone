# ASHA EHR Companion - Mobile Healthcare App

## Problem Statement
**SIH 2025 Problem Statement ID**: 25219  
**Title**: Mobile-based EHR Companion for ASHA Workers in Low-Internet Areas  
**Organization**: Ministry of Science and Technology  
**Department**: Department of Science and Technology (DST)  
**Category**: Software  
**Theme**: MedTech / BioTech / HealthTech

## Overview
ASHA EHR Companion is an offline-first mobile web application designed for ASHA (Accredited Social Health Activist) workers in rural India to manage electronic health records in areas with poor or no internet connectivity.

## Key Features
- **Offline-First Architecture**: Store and manage patient data locally using IndexedDB
- **Automatic Sync**: Seamlessly sync data when internet connection is restored
- **Multilingual Support**: Full interface support for English, Hindi, Tamil, and Bengali
- **Voice Input**: Speech-to-text capability for easier data entry in local languages
- **Patient Management**: Complete CRUD operations for patient records
- **Visit Tracking**: Record patient visits with symptoms, diagnosis, and vital signs
- **Vaccination Management**: Track vaccination schedules and remind workers of pending doses
- **ANC (Antenatal Care)**: Monitor pregnancy checkups with detailed health metrics
- **Smart Reminders**: Automatic reminders for vaccinations, ANC visits, and follow-ups
- **Mobile-Optimized**: Touch-friendly Material Design interface optimized for smartphones
- **PWA Support**: Installable as a Progressive Web App for native-like experience

## Technology Stack

### Frontend
- **React 18** with TypeScript
- **Wouter** for client-side routing
- **TanStack Query** for data fetching and caching
- **Dexie.js** for IndexedDB offline storage
- **i18next** for internationalization
- **Shadcn UI** + Tailwind CSS for beautiful, accessible components
- **Web Speech API** for voice input
- **Material Design** principles for mobile UX

### Backend
- **Node.js** with Express
- **PostgreSQL** (Neon) for persistent storage
- **Drizzle ORM** for type-safe database operations
- **Zod** for runtime validation

## Project Structure
```
├── client/
│   ├── src/
│   │   ├── components/      # Reusable UI components
│   │   ├── pages/          # Page components (Dashboard, Patients, etc.)
│   │   ├── hooks/          # Custom React hooks
│   │   ├── i18n/           # Internationalization config
│   │   ├── lib/            # Utilities (offline DB, sync service)
│   │   └── App.tsx         # Main app component
│   └── index.html
├── server/
│   ├── db.ts              # Database connection
│   ├── storage.ts         # Data access layer
│   └── routes.ts          # API endpoints
├── shared/
│   └── schema.ts          # Shared types and schemas
└── design_guidelines.md   # Design system documentation
```

## Database Schema

### Patients
- Basic demographics (name, age, gender)
- Contact information (phone, address, village)
- Sync status tracking

### Visits
- Patient visit records with symptoms and diagnosis
- Vital signs (blood pressure, temperature, weight)
- Visit notes

### Vaccinations
- Vaccine name and dose number
- Scheduled and administered dates
- Status tracking (pending, completed, overdue)

### ANC Checkups
- Pregnancy checkup records
- Gestational age, vital signs
- Test results (hemoglobin, urine)
- Complications tracking

### Reminders
- Type-based reminders (vaccination, ANC, follow-up)
- Due dates and status
- Description and notes

## API Endpoints

### Patients
- `GET /api/patients` - List all patients
- `GET /api/patients/:id` - Get single patient
- `POST /api/patients` - Create patient
- `PATCH /api/patients/:id` - Update patient
- `DELETE /api/patients/:id` - Delete patient

### Visits
- `GET /api/visits?patientId=:id` - Get visits for patient
- `POST /api/visits` - Create visit

### Vaccinations
- `GET /api/vaccinations?patientId=:id` - Get vaccinations for patient
- `POST /api/vaccinations` - Schedule vaccination
- `PATCH /api/vaccinations/:id` - Update vaccination

### ANC Checkups
- `GET /api/anc-checkups?patientId=:id` - Get ANC checkups for patient
- `POST /api/anc-checkups` - Record ANC checkup

### Reminders
- `GET /api/reminders` - Get all reminders
- `POST /api/reminders` - Create reminder
- `PATCH /api/reminders/:id` - Update reminder
- `DELETE /api/reminders/:id` - Delete reminder

### Sync
- `GET /api/sync/status` - Get sync status and pending count
- `POST /api/sync/upload` - Batch upload offline data

## Offline-First Architecture

### Data Flow
1. **User Action**: User creates/updates record in the app
2. **Local Storage**: Data immediately saved to IndexedDB
3. **Optimistic UI**: UI updates instantly for responsive feel
4. **Background Sync**: When online, data automatically syncs to server
5. **Conflict Resolution**: Server IDs replace local IDs after successful sync

### Sync Strategy
- All CRUD operations work offline
- Data marked with `synced: false` when created offline
- Automatic sync triggered when device comes online
- Manual sync available via sync button
- Visual indicators show pending sync count

## Development Setup
```bash
# Install dependencies
npm install

# Push database schema
npm run db:push

# Start development server
npm run dev
```

## Design System
The app follows Material Design principles with a healthcare-optimized color palette:
- **Primary**: Teal (#14b8a6) - Healthcare trust and professionalism
- **Success**: Green - Completed actions
- **Warning**: Orange - Pending items
- **Danger**: Red - Overdue/critical items

### Touch Targets
- Minimum 48x48px (h-12) for all interactive elements
- Large, easy-to-tap buttons and form inputs
- Generous spacing (p-4, p-6) for comfortable mobile use

### Typography
- Roboto font family for clean, professional appearance
- Clear hierarchy with proper sizing (text-2xl, text-xl, text-base)
- High contrast for outdoor readability

## Multilingual Implementation
The app supports 4 languages out of the box:
- **English**: Default language
- **Hindi**: हिंदी
- **Tamil**: தமிழ்
- **Bengali**: বাংলা

Language switcher is accessible from the top app bar. All UI strings are fully translated including form labels, buttons, and messages.

## Voice Input Feature
Powered by the Web Speech API, users can:
- Tap the microphone icon on any text input
- Speak in their preferred language
- Auto-transcription fills the input field
- Works for patient names, symptoms, addresses, and more

## Recent Changes
- ✅ Complete database schema with relations
- ✅ Offline-first IndexedDB implementation
- ✅ Automatic sync service with background sync
- ✅ All API endpoints with validation
- ✅ Multilingual support (4 languages)
- ✅ Voice input integration
- ✅ Mobile-optimized Material Design UI
- ✅ Bottom navigation for mobile UX
- ✅ Sync status indicator with pending count
- ✅ Empty states and loading skeletons

## Future Enhancements
- [ ] Biometric patient identification
- [ ] GPS-based visit tracking
- [ ] Integration with national health programs (CoWIN, HMIS)
- [ ] Advanced analytics dashboard
- [ ] End-to-end encryption for ABDM compliance
- [ ] Supervisor/PHC staff portal
- [ ] WhatsApp/SMS integration for patient reminders

## User Preferences
- Mobile-first design with touch-optimized interface
- Offline capability is critical for field work
- Simple, intuitive UI for users with varying tech literacy
- Visual feedback for all actions
- Minimal data entry friction with voice input
