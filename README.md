# ExamDesk – Online Exam System (front-end demo)

Pure HTML, CSS and JavaScript. No backend, no build step. All data is stored in the browser's LocalStorage.

## How to run
1. Unzip the folder.
2. Double-click `index.html` (or serve the folder with any static server).
3. Pick **Student portal** or **Admin portal**.

## Demo logins
| Portal  | Login                          | Password     |
|---------|--------------------------------|--------------|
| Admin   | `admin`                        | `admin123`   |
| Student | `STU2024001` or `aarav@example.com` | `student123` |
| Student | `STU2024002` (Meera, has a failed attempt) | `student123` |

You can also register a new student from the student login page.

## Sample data
5 exams are created on first load: JavaScript Fundamentals (8 Q), HTML & CSS Basics (6 Q), General Aptitude (6 Q),
Computer Fundamentals (draft, hidden from students) and Data Structures Mid-Term (scheduled 3 days ahead, shown as "upcoming"), plus 3 sample results.

## Structure
```
index.html              Landing page (Student / Admin portal)
css/style.css           Shared design system, light + dark themes, responsive rules
js/storage.js           LocalStorage data layer (students, exams, results, notifications, activity)
js/common.js            Toasts, modals, confirm dialogs, theme, icons, charts, notifications
js/student-auth.js      Student login / register + validation
js/student-dashboard.js Student dashboard (overview, exams, results, profile)
js/instructions.js      Exam instructions page
js/exam.js              Timed exam engine (shuffle, auto-save, auto-submit, refresh guard)
js/result.js            Result page with answer review
js/admin.js             Admin panel (overview, exams, questions, students, results, activity, settings)
student/                login, dashboard, instructions, exam, result pages
admin/                  login + dashboard pages
```

## Data separation
- Student session: `ex_session_student`. Admin session: `ex_session_admin`. Each portal guards its own pages.
- In-progress exams (auto-saved answers + timer end time) are stored per student under `ex_attempt_<studentId>`.
- Students only see exams that are **published** and whose opening date (if set) has passed.

## Notes
- Passwords use a simple demo hash. A production system must hash and verify passwords on a server.
- Clearing browser data removes everything; **Admin → Settings → Reset all data** restores the samples.
- Google Fonts load when online; the layout falls back to system fonts offline.
