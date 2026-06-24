SERAS — Smart Event Registration & Attendance System (Agent Prompt)
This document is a comprehensive system prompt and interface specification for the SERAS (Smart Event Registration & Attendance System) website. It is designed to guide autonomous AI agents (such as browser subagents or LLMs) to navigate, test, and interact with the platform seamlessly.

🌐 Environment & Accessibility
Local Address: http://localhost:5173
Global Network Access (Localtunnel): https://dry-eyes-help.loca.lt
Admin Bypass PIN: 1234 (required to unlock the Admin Dashboard)
🛠 Tech Stack & UI Conventions
Frontend Framework: React 19 (Vite), Tailwind CSS (sleek dark mode / glassmorphism, responsive colors).
Navigation Layouts:
PC/Laptop (Desktop): A premium bottom-centered MacOS-style magnification dock with spring physics hover effects.
Mobile: A floating side drawer (Sidebar) and a simple top bar header.
Micro-Animations: Fluid page transitions (crossfade/slide) handled via Framer Motion, and 3D hover lifting on cards.
Database & Auth: Supabase-backed real-time database with active Session and Profile contexts.
PWA Capabilities: Fully-functional Progressive Web App with off-line asset caching and push notifications.
📂 Routes & Page Details
🏠 Home Page (/)
Purpose: Central hub displaying upcoming academic and campus events.
Interactions:
Search bar to filter events.
Staggered entrance animation for event cards.
Clicking an event card redirects to the Event Details page (/event/:id).
Clicking the heart icon on any card toggles saving the event to /favorites.
📚 Event Details Page (/event/:id)
Purpose: Full information page for a specific event (date, time, venue, speaker details, and registration link).
Interactions:
"Register Now" button redirects to the registration form (/register/:eventId).
Contains organizer contact links and descriptions.
"Set Reminder" triggers a browser-level notification alert.
📝 Registration Page (/register/:eventId)
Purpose: Form for participants to submit registrations.
Fields: Full Name, Email, Student ID, Department.
Verification Workflow:
Click "Send Verification Code".
Backend triggers an email with a 6-digit OTP code.
Input the OTP code and click "Verify OTP".
On successful verification, click "Complete Registration" to generate the QR ticket (/ticket/:regId).
🎫 Ticket & Check-In Page (/ticket/:regId)
Purpose: Renders the user's digital entry ticket with a unique generated QR code.
Interactions:
Display check-in status ("Pending" or "Attended").
"Download Ticket" / "Save QR" option.
"Generate ID Card" option: creates a downloadable digital badge combining user profile photo and event details.
🔑 Admin Dashboard (/admin)
Purpose: Secure workspace for administrators to manage the platform.
Access Control: Requires logging in and entering the Admin PIN: 1234 if prompted.
Features:
Table showing all registered participants for all events.
Export registered user lists as CSV.
Action buttons to approve, edit, or remove events.
Navigation buttons to the QR Scanner (/admin/scanner), Create Event (/admin/create-event), and Analytics (/admin/analytics).
📷 QR Scanner Page (/admin/scanner)
Purpose: Camera check-in utility for admins to scan participant tickets at the venue door.
Interactions:
Scans user QR code.
Validates registration status against Supabase.
Instantly marks attendance as "Attended" and provides sound/visual confirmation.
📊 Admin Analytics Page (/admin/analytics)
Purpose: Displays registration trends, attendance rates, and feedback rating distributions.
Visuals: Custom visual charts and graphs powered by React SVG components.
👨‍🏫 Faculty Directory (/faculty)
Purpose: Profiles of college faculty members and professors.
Interactions:
Quick action buttons: Call (opens dialer), Email (opens mailto client), and Message (redirects to in-app messages).
💬 Messages Page (/messages)
Purpose: Real-time in-app chats between students and faculty/organizers.
🏆 Portfolio / Profile Page (/profile)
Purpose: Student hub summarizing their participation history.
Features:
Section showing upcoming registered events and tickets.
Section displaying attended events with "Claim Certificate" buttons.
User details editor (Name, ID, Department, and Profile Picture upload).
✍️ Feedback & Certificate Page (/feedback/:eventId)
Purpose: Feedback form for attended events.
Interactions:
Star ratings (1-5 stars) and textarea comments.
Submitting feedback unlocks the downloadable participation certificate (generated client-side via canvas with official styling).
🤖 Instructions for AI Agents Visiting the Site
Accessing Content:
Always load http://localhost:5173 or the active tunnel https://dry-eyes-help.loca.lt.
Utilize the bottom dock (desktop) or sidebar menu (mobile) to jump between pages.
Performing Check-ins:
To test check-in, register a test user, copy the ticket ID/QR code string, then log into the /admin portal (PIN 1234), navigate to /admin/scanner, and manually input the code or scan the QR.
Form Submissions:
Input valid details. For OTP tests, note that the backend OTP code is logged or standard dev bypass rules apply depending on env.
Interacting with Helper AI:
A floating robot icon is situated in the bottom right corner (HelperAI).
Agents can click this bubble to activate a helper bot capable of responding to questions about registrations, tickets, check-in, certificates, and more.
