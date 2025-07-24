# Transportes M&M - Fleet Management Application

## Overview

This is a comprehensive fleet management application built for "Transportes M&M" - a Spanish-language web and mobile application designed to manage weekly operations for an Uber fleet. The system serves two main user types: administrators (Miguel) and drivers, providing functionality for income tracking, deductions management, direct communication, automated ticket generation, and complete visual customization.

## User Preferences

Preferred communication style: Simple, everyday language. Prefers dark theme as default for the application.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Radix UI components with shadcn/ui styling system
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **Routing**: Wouter for client-side routing
- **State Management**: TanStack Query (React Query) for server state management
- **Form Handling**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript throughout the entire stack
- **Database**: PostgreSQL with Neon Database as the cloud provider
- **ORM**: Drizzle ORM for type-safe database operations
- **Real-time Communication**: WebSocket implementation for live chat and notifications
- **Authentication**: Session-based authentication with bcrypt password hashing
- **File Uploads**: Multer for handling image uploads (driver photos, etc.)

## Key Components

### Database Schema
- **Users Table**: Stores authentication and basic user information
- **Drivers Table**: Driver-specific information linked to users
- **Tickets Table**: Weekly financial records with income, deductions, and calculations (includes audit fields created_by/updated_by)
- **Messages Table**: Direct messaging between admin and drivers
- **Communications Table**: Broadcast messages from admin to all drivers
- **Communication Reads Table**: Tracking read status of broadcast messages

### Authentication System
- Role-based access control (admin vs driver)
- Multi-administrator support (up to 3 admins)
- Session management with express-session
- Protected routes based on user roles
- Automatic redirection based on authentication status
- Admin management interface for creating/editing/deleting other admins

### Real-time Features
- WebSocket server for instant messaging
- Live notifications for new messages and communications
- Real-time updates for ticket status changes

## Data Flow

1. **Authentication Flow**: Users log in through a unified login page, then are redirected to role-appropriate dashboards
2. **Admin Management**: Primary admin can create up to 3 total administrators with full system access
3. **Ticket Generation**: Any admin creates weekly tickets with income, deductions, and automatic tax calculations (audit trail records creator)
4. **Communication Flow**: Bidirectional messaging between admin and drivers, plus broadcast communications
5. **PDF Generation**: Client-side PDF generation for ticket downloads using jsPDF
6. **File Upload**: Images can be uploaded for tickets and stored on the server
7. **Audit Trail**: All ticket operations track which admin user created or modified each record

## External Dependencies

### Database
- **Neon Database**: PostgreSQL-compatible cloud database
- **Connection**: Uses connection pooling with @neondatabase/serverless

### UI Components
- **Radix UI**: Comprehensive set of accessible UI primitives
- **Lucide React**: Icon library for consistent iconography
- **TailwindCSS**: Utility-first CSS framework

### Development Tools
- **Drizzle Kit**: Database migrations and schema management
- **ESBuild**: Fast JavaScript bundler for production builds
- **Replit Integration**: Development environment with live reload and error handling

## Deployment Strategy

### Development Environment
- Hot reload with Vite development server
- WebSocket support for real-time features
- Automatic database migrations with Drizzle

### Production Build
- Client-side assets built with Vite and served statically
- Server-side code bundled with ESBuild
- Environment variables for database connections and secrets
- Session store configuration for production scaling

### Key Features
- **Responsive Design**: Works on both desktop and mobile devices
- **Multi-language Support**: Spanish language throughout the interface
- **Multi-Administrator System**: Support for up to 3 administrators with full audit trail
- **PDF Export**: Generate and download formatted weekly tickets
- **Real-time Chat**: Instant messaging between admin and drivers
- **File Upload**: Support for image attachments
- **Custom Theming**: Brand-specific colors and styling for Transportes M&M
- **Audit Trail**: Complete tracking of who created/modified each ticket

## Recent Changes (July 2025)

- **URL de Acceso Móvil Corregida (July 22, 2025)**:
  - Identificado problema DNS con URL incorrecta: `transport-logistics-mono240306.replit.dev`
  - URL correcta verificada: `d027c0f3-ab9a-4f71-a0a9-5140088b7d96-00-2oso9nxp16h7.worf.replit.dev`
  - Creadas páginas de respaldo para dispositivos móviles: `simple-test.html` y `mobile-test.html`
  - Sistema de diagnóstico móvil implementado para resolver problemas de conectividad
  - Múltiples fallbacks implementados para garantizar acceso desde cualquier dispositivo

- **Application Stability Fixes (July 21, 2025)**:
  - Fixed critical React errors causing blank screens for drivers after extended use
  - Implemented comprehensive Error Boundaries throughout the application
  - Enhanced session management with 30-day cookie duration for mobile stability
  - Added StableSessionManager component for automatic session renewal
  - Improved authentication middleware with session validation and cleanup
  - Enhanced NotificationManager with robust error handling and reconnection logic
  - Fixed WebSocket connection stability with exponential backoff reconnection
  - All components now wrapped in error boundaries to prevent app crashes
  - Session now automatically refreshes user data on each authentication check
- **Multi-Administrator Implementation**: Added support for multiple administrators (up to 3 total)
- **Audit Trail System**: Added created_by and updated_by fields to tickets table
- **Admin Management Interface**: New dashboard section for creating/editing/deleting admin users
- **Ticket Attribution**: All tickets now show who created and last modified them
- **Enhanced Security**: Admins cannot delete themselves, preventing system lockout
- **Brand Integration**: New company logo integrated throughout the application (login, dashboards, tickets)
- **Visual Theme Update**: Updated color scheme to match the golden helmet logo with navy blue theme
- **Dark Theme Default**: Configured dark theme as the system default with background #1a1a1a and white text
- **Global Theme Application**: Theme changes by administrators now apply to all users (drivers and admins)
- **Button Visibility Fixes**: Fixed login and theme management buttons with proper colors (amber for login, blue for save, gray for reset)
- **Theme Persistence**: All theme settings are stored in database and apply across user sessions
- **PWA Implementation**: Progressive Web App configuration for mobile installation
- **Push Notifications**: Real-time notifications for ticket releases and chat messages
- **Ticket Deletion**: Admin functionality to select and delete multiple tickets with confirmation
- **Driver Profile Photos**: Ability to upload and display driver profile photos in admin dashboard and chat system
- **Enhanced Chat Avatars**: Driver photos displayed in chat messages and conversation headers
- **Real-time Location Sharing**: Both admins and drivers can view all connected drivers' locations on interactive maps
- **Driver-to-Driver Visibility**: Drivers can see each other's locations in real-time for better coordination
- **Initial Setup System**: Added automatic first-time administrator registration when no admins exist in the system
- **Setup Page Protection**: System automatically redirects to setup page when no administrators are configured
- **Auto-login After Setup**: First administrator is automatically logged in after initial configuration
- **Setup Detection API**: /api/auth/needs-setup endpoint properly detects when system requires initial configuration  
- **Database Reset Capability**: System can be reset to initial state for fresh administrator registration
- **Production Ready**: First administrator successfully created with full system access and auto-login functionality
- **Driver Management Fixes**: Resolved FormData parsing issues in backend for proper driver creation
- **Enhanced UI**: Green buttons for driver creation/management with improved visibility and user experience
- **Driver CRUD Operations**: Full create, read, update, delete functionality for driver management with confirmation dialogs
- **Enhanced Button Visibility**: Implemented highly visible green buttons with forced CSS styling for driver creation and management
- **Critical Ticket Calculation Bug Fixed (July 22, 2025)**: 
  - Identified and corrected serious calculation error in Daniel Silvestre's ticket
  - Weekly rent was stored as negative value (-2500.00) causing incorrect positive net total
  - Corrected calculation: Platform Income (5300.23) - Weekly Rent (2500.00) - Total Debts (4270.41) = Net Total (-1470.18)
  - Driver now correctly shows negative balance as expected when debts exceed income
  - Database updated to show proper negative net total reflecting actual financial position
- **Visual Enhancement for Net Total Colors (July 22, 2025)**:
  - Implemented conditional color coding for total neto display across all components
  - Green color for positive net totals (driver earns money)
  - Red color for negative net totals (driver owes money)
  - Applied consistently in ticket previews, driver portal, admin reports, and creation modals
  - Daniel Silvestre's ticket now correctly displays -$1,470.18 in red as expected
- **Complete Black Text Implementation in Ticket Modal (July 22, 2025)**:
  - Forced all text elements in ticket creation modal to display in black
  - Added ultra-specific CSS rules with !important declarations
  - Applied inline styles to all labels, inputs, selects, and text elements
  - Implemented Radix UI component overrides for proper text color
  - Added .ticket-modal class for targeted styling
  - Ensured complete visibility and readability in admin interface
- **Button Styling Issues Resolved**: Applied inline styles to ensure green buttons appear consistently across all environments
- **Driver Deletion Cascade**: Fixed foreign key constraint issues by implementing proper deletion cascade for drivers and their associated tickets
- **Password Update System Fixed (July 20, 2025)**: Resolved double-hashing issue in driver password updates:
  - Fixed duplicate password hashing between routes.ts and storage.ts
  - Added intelligent password detection to prevent double-hashing
  - Updated storage.updateUser to check if password is already hashed
  - Manually corrected existing driver passwords (Keke, Potra, Oso, Hec) to work properly
  - System now properly handles all new driver password updates
- **Complete Driver Management Rewrite (July 20, 2025)**: Completely rewrote driver management interface with specific mobile-optimized design:
  - Large blue button "Agregar Conductores" with white text (#2563eb background)
  - Modal with white background and black text for optimal mobile visibility
  - Photo upload functionality with circular preview
  - Organized form layout with proper spacing for mobile devices
  - Fixed export/import issues for proper component loading
  - Server restart and rebuild for mobile URL compatibility
- **Mobile Android/iOS Compatibility Issues Resolved (July 20, 2025)**: 
  - Identified DNS resolution problems with development URLs on mobile devices
  - Implemented comprehensive PWA (Progressive Web App) configuration
  - Added Service Worker for offline functionality and mobile optimization
  - Created mobile-specific meta tags for iOS and Android compatibility
  - Built production-ready application bundle for deployment
  - **FINAL SOLUTION**: Stable mobile URL identified and documented
  - URL: `https://d027c0f3-ab9a-4f71-a0a9-5140088b7d96-00-2oso9nxp16h7.worf.replit.dev`
  - **Complete Driver Editing Functionality Implemented (July 20, 2025)**:
    * Blue "Edit" button on each driver card
    * Reusable modal for create/edit operations  
    * FormData backend handling with photo upload support
    * Optional password updates (leave blank to maintain current)
    * Full validation and error handling
    * Mobile-optimized interface with proper button visibility
- **Custom Logo Integration and PWA Auto-Installation (July 20, 2025)**:
  - Integrated user's custom golden spartan helmet logo as official app icon
  - Configured manifest.json with custom logo in standard sizes (192px, 512px)
  - Optimized PWA installation for automatic prompt display without manual menu access
  - Added intelligent prompt timing with 24-hour cooldown for dismissed installations
  - Enhanced beforeinstallprompt detection for seamless user experience
  - Logo appears as app icon, favicon, and in push notifications
  - Confirmed automatic installation prompt working correctly on Android/Chrome
- **GPS Location System Completely Operational (July 20, 2025)**:
  - Fixed admin dashboard GPS map displaying blank screen issue
  - Created simplified real-time map component (RealTimeMapSimple) without dependency conflicts
  - Admin dashboard now correctly shows connected drivers with live GPS coordinates
  - Driver "Potra" (Carlos Vega) confirmed active and visible in admin panel
  - Real-time location updates every 3 seconds with WebSocket synchronization
  - Service Worker implemented for persistent GPS tracking in background
  - Visual indicators: green badges for online drivers, red for offline
  - Interactive map with driver markers and click-to-center functionality
  - Comprehensive driver list showing names, codes, coordinates, and last update times
  - **CONFIRMED WORKING**: User screenshot shows complete GPS map with Attitud marker visible, grid background, compass, and real-time coordinates (19.4326, -99.1332)
- **Complete Data Backup and Recovery System (July 21, 2025)**:
- **Automated Monthly Backup System (July 21, 2025)**:
  - Implemented comprehensive backup system for complete data protection
  - JSON-based backup format including all critical data: users, drivers, tickets, messages, communications, GPS locations
  - Admin dashboard backup card with one-click backup creation and download
  - Backup APIs for create, list, download, and delete operations with proper authentication
  - Automatic file management with timestamps and size information
  - Successfully tested: created backup with 10 users, 8 drivers, 2 communications, 5 GPS locations
  - Backup files stored securely in `/backups/` directory accessible only to authenticated administrators
  - Mobile-compatible interface for backup management across all devices
  - **Google Drive Integration**: Automatic upload to Google Drive with credentials configuration
  - **Smart Cloud Management**: Maintains 12 most recent backups (annual coverage) in Google Drive and locally
  - **Hybrid Storage**: Local + Cloud backup strategy for maximum data protection
  - **JSON Format**: Human-readable backup files that can be opened on any device
  - **PRODUCTION READY**: Complete backup system operational with local and cloud storage options
  - **Automated Monthly Scheduling**: Implemented cron-based automatic backup system
  - **Scheduled Execution**: Day 1 of each month at 2:00 AM Mexico City timezone  
  - **Space Calculation Engine**: Real-time calculation of Google Drive storage requirements (~100 MB annually)
  - **Smart Growth Estimation**: Accounts for business growth with ticket, message, and GPS data expansion
  - **Development Testing**: Manual test function for automatic backup verification
  - **Annual Coverage**: 12-month protection cycle with automatic old backup cleanup
- **UI/UX Improvements (July 21, 2025)**:
  - **Date Display Fix**: Resolved date desfase issue where selected dates (14-20 July) showed as 13-19 July
  - **Backend Date Processing**: Fixed timezone conversion by adding 'T00:00:00' to date strings in server routes
  - **Frontend Date Display**: Applied consistent date formatting across all components (tickets, reports, PDF generation)
  - **Total Neto Styling**: Enhanced visual presentation with dark green background box (#bg-green-800)
  - **Text Color Standardization**: All editable fields (concepts, amounts) now display in black text for better visibility
  - **Cross-Component Consistency**: Date and styling fixes applied to admin panel, driver view, reports, and PDF exports
- **GPS Automático y Geocodificación Implementados (July 22, 2025)**:
  - FUNCIONALIDAD NUEVA: GPS automático se activa al entrar al sistema como chofer
  - Tracking continuo cada 2 minutos + detección de cambios de ubicación significativos
  - Geocodificación inversa implementada - muestra calles y direcciones reales de cada chofer
  - API gratuita de OpenStreetMap para convertir coordenadas a direcciones (Nominatim)
  - GPS funciona en background cuando app está minimizada con detection de visibilidad
  - Notificaciones discretas de actualización GPS en tiempo real
  - Formato de direcciones: "Calle Nombre 123, Colonia, Ciudad" + coordenadas exactas
  - Sistema optimizado para Android con configuraciones de alta precisión y timeouts ajustados
- **Sistema de Tickets Móvil Completamente Funcional (July 22, 2025)**:
  - PROBLEMA RESUELTO: Error 500 eliminado de API móvil de tickets
  - Implementada consulta SQL directa para carga confiable de tickets por chofer
  - Interface visual mejorada sin código JSON técnico confuso para choferes
  - Confirmado funcionamiento: Daniel (DanyFlow) y Hector (Hec) acceden correctamente
  - Todos los choferes pueden ver tickets con información financiera clara (colores verde/rojo)
  - Sistema username/password completamente estable para acceso móvil
- **Emergency Login Fix and Resolution (July 22, 2025)**:
  - ISSUE IDENTIFIED: Missing admin user in database caused login failures
  - ISSUE RESOLVED: Updated Leonidas admin credentials to username/password: Leonidas/admin
  - React Hook Form working correctly after database user correction
  - Implemented dual authentication system:
    * Normal form login for administrators (Leonidas/admin)
    * Direct username/password access for drivers using their existing credentials
  - Drivers use their standard usernames (DanyFlow, Ivan, Keke, Potra, Oso, Hec) with personal passwords
  - Green access button "👨‍💼 ACCESO CHOFER" for drivers
  - System fully operational with admin successfully accessing dashboard
  - All authentication methods confirmed working in production environment
  - User preference: Drivers prefer username/password over PIN system
- **Driver Ticket Access Fixed (July 22, 2025)**:
  - ISSUE: Drivers could login but couldn't see their assigned tickets (Error 401)
  - ROOT CAUSE: Storage.getTicketsByDriver() function had structural issues preventing ticket retrieval
  - SOLUTION: Implemented direct SQL query in mobile API bypassing problematic storage functions
  - VERIFICATION: Confirmed Hector (Hec) has 1 ticket with $1,402.89 net total in database
  - Mobile API now uses direct database queries for reliable driver ticket filtering
  - Simplified token validation system for better mobile compatibility
  - Drivers can now successfully view their personalized ticket information
  - **Production Sync Issue Resolved (July 22, 2025)**:
    * Identified server was running in development mode causing preview/production URL differences
    * Forced static file serving mode to ensure compiled code with driver section is served
    * Confirmed driver access section present in compiled JavaScript bundle (index-DmzhBgL0.js)
    * Production URL now serves complete interface with both admin login and driver PIN access
- **Preview URL Fix and Ticket Validation (July 22, 2025)**:
    * Removed conflicting promotional HTML file (server/public/index.html) that was overriding main application
    * Fixed ticket creation validation to allow $0 platform income (Jorge Montes case resolved)
    * Updated Zod validation to accept numeric values ≥ 0 for platformIncome and weeklyRent
    * Application now correctly serves from compiled dist/public/ directory
- **Complete Driver Personalization Implemented (July 23, 2025)**:
    * Implemented full functionality for drivers to see their photo and name when logging in
    * PC Driver Portal Header: Added personalized header with circular profile photo, full name, and driver code
    * Mobile Header Enhancement: Updated mobile version to show user avatar, complete name, and role information
    * API Endpoint Creation: Developed `/api/drivers/me` endpoint to provide personalized driver information
- **Enhanced Session Management System (July 23, 2025)**:
    * ISSUE RESOLVED: Fixed session loss problem after periods of inactivity that caused application to become unresponsive
    * Enhanced Session Configuration: Extended session duration to 90 days with automatic renewal system
    * SessionManager Component: New intelligent session management with automatic recovery and activity detection
    * Session Recovery Page: Dedicated recovery interface at `/session-recovery.html` for handling session interruptions
    * Automatic Session Backup: Local storage backup system maintains session data for up to 7 days
    * Activity-Based Renewal: Sessions automatically extend based on user activity (mouse, keyboard, touch events)
    * Proactive Session Validation: Every 5 minutes verification with exponential backoff retry logic
    * Mobile Session Stability: Improved session persistence specifically optimized for Android devices
    * Error Handling: Graceful degradation with user-friendly recovery options and clear error messages
- **GPS Location System Completely Fixed (July 23, 2025)**:
    * ISSUE RESOLVED: GPS locations not updating when drivers connect to the application
    * Enhanced Location Broadcast: Improved WebSocket broadcasting with detailed logging and connection counting
    * Automatic GPS Activation: New GPSAutoActivator component automatically starts GPS tracking for drivers upon login
    * Real-time Location Updates: Enhanced query refresh system with aggressive 3-second intervals and background updates
    * Persistent GPS Tracking: Improved PersistentGPS system with better error handling and network change detection
    * WebSocket Location Handling: Added locationUpdate message processing in NotificationManager for instant map updates
    * Server-side Logging: Enhanced location API with detailed console logging for debugging and monitoring
    * Dual GPS System: Combined automatic activation with manual controls for maximum reliability
    * Mobile Optimization: Visibility change detection to restart GPS when app returns to foreground
- **Android APK Development Complete (July 23, 2025)**:
    * MILESTONE ACHIEVED: Complete APK infrastructure ready for Google Play Store deployment
    * Capacitor 7.4.2 Integration: Full Android project initialized with professional configuration
    * Native Android Manifest: All GPS, notification, and internet permissions properly configured
    * Custom Logo Integration: Golden spartan helmet logo installed in all required Android resolutions
    * Gradle Build System: Complete build configuration with debug and release variants
    * App Store Ready: Package ID "com.transportesmm.fleet" registered and configured
    * Professional Assets: Splash screen, app icons, and theme colors matching brand identity
    * Native Plugin Integration: GPS, notifications, haptics, keyboard, and camera plugins installed
    * Production Commands: Scripts ready for generating debug APK and release AAB for Play Store
    * Complete Documentation: Step-by-step guides for Google Play Store submission and management

The application follows a monorepo structure with shared TypeScript types and schemas between client and server, ensuring type safety across the entire stack. The architecture supports both web and future mobile app development while maintaining a clean separation of concerns between different application layers.