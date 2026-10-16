# CodeArena — Online Judge Platform

A full-stack competitive programming platform built to help developers practice coding, execute solutions, solve programming problems, and track their progress in one place.

**Repository:** [Pragati4566/CodeArena](https://github.com/Pragati4566/CodeArena)

<p align="left">
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=flat&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Node.js-Backend-339933?style=flat&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Express.js-API-000000?style=flat&logo=express&logoColor=white" alt="Express.js" />
  <img src="https://img.shields.io/badge/MongoDB-Database-47A248?style=flat&logo=mongodb&logoColor=white" alt="MongoDB" />
  <img src="https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=flat&logo=javascript&logoColor=black" alt="JavaScript" />
</p>

## Overview

CodeArena is a web-based online judge designed around the coding practice workflow. It brings together a problem-solving interface, an integrated code editor, a backend API, a database, and a compiler service.

The platform supports multiple programming languages and allows users to write solutions, execute code against test cases, submit answers, and review their results.

The project combines frontend development, backend engineering, database management, authentication, and code execution into a single application.

## Features

### 1. Coding and Problem Solving

- Browse programming problems and their descriptions.
- Solve problems across Easy, Medium, and Hard difficulty levels.
- Write code using an integrated Monaco Editor.
- Benefit from syntax highlighting and editor autocomplete.
- Execute code against test cases.
- Submit solutions and inspect their verdicts.

### 2. Multi-Language Code Execution

CodeArena supports the following programming languages:

- **C++** — compiled execution.
- **Java** — compiled execution.
- **Python** — interpreted execution.

A dedicated compiler service handles code execution separately from the main application backend.

### 3. User Authentication and Profiles

- User registration and login.
- JWT-based authentication.
- Password hashing.
- User profiles and submission history.
- Role-based access for users and administrators.
- Coding progress and performance statistics.

### 4. Submission Tracking and Rankings

- Maintain a history of submitted solutions.
- Review submission verdicts.
- Track problem-solving activity.
- Organize problems by difficulty.
- View leaderboard rankings and available performance statistics.

### 5. Administrative Dashboard

Administrative functionality supports platform management, including:

- Creating, updating, and deleting programming problems.
- Managing test cases associated with problems.
- Viewing user information and managing roles.
- Maintaining problem and platform data.

### 6. User Interface

- React-based frontend.
- Responsive layouts with Tailwind CSS.
- Monaco Editor integration.
- React Router-based navigation.
- Theme support and editor customization.
- User feedback through notifications.

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React 19, JavaScript, Tailwind CSS |
| Code Editor | Monaco Editor |
| Routing | React Router DOM |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Authentication | JSON Web Tokens (JWT) |
| Password Security | bcrypt |
| Input Validation | Joi |
| Compiler Service | Node.js-based execution service |
| Frontend Build Tool | Vite |

## System Architecture

CodeArena uses a modular architecture that separates the user interface, application backend, code execution service, and persistent storage.

```text
                   ┌─────────────────────────┐
                   │       User / Browser    │
                   └────────────┬────────────┘
                                │
                                ▼
                   ┌─────────────────────────┐
                   │     React Frontend      │
                   │   Monaco Code Editor    │
                   └────────────┬────────────┘
                                │
                      API Requests / Responses
                                │
                                ▼
                   ┌─────────────────────────┐
                   │    Express Backend      │
                   │ Authentication & APIs   │
                   └──────────┬───────┬──────┘
                              │       │
                              ▼       ▼
                    ┌────────────┐  ┌───────────────┐
                    │  MongoDB   │  │ Compiler      │
                    │  Database  │  │ Service       │
                    └────────────┘  └───────┬───────┘
                                            │
                                            ▼
                                   Code Execution
                                 C++ / Java / Python
```

### Application Flow

1. A user selects a programming problem and writes a solution in the code editor.
2. The frontend communicates with the backend through API requests.
3. The compiler service processes the code using the selected language.
4. The execution results are returned to the application.
5. The submission workflow uses the relevant test cases and verdicts to evaluate the solution.
6. User and submission information is stored in MongoDB where required.

## Database Overview

The application uses MongoDB to manage its main application data.

| Entity | Purpose |
|---|---|
| Users | Account information, roles, and profile statistics |
| Problems | Problem statements, difficulty, and associated metadata |
| Submissions | Submitted code, programming language, verdict, and execution details |
| Test Cases | Inputs and expected outputs used to evaluate solutions |

The exact schema and relationships depend on the corresponding models implemented in the application.

## Getting Started

Follow these steps to run the project locally.

### Prerequisites

Install the following tools before starting:

- Node.js and npm.
- MongoDB, running locally or through a configured database service.
- A C++ compiler, such as `g++`.
- Java Development Kit (JDK).
- Python 3.
- Git.

Ensure the language runtimes are available to the compiler service through your system's `PATH`.

### 1. Clone the Repository

```bash
git clone https://github.com/Pragati4566/CodeArena.git
cd CodeArena/Online-Judge-main
```

### 2. Configure the Backend

```bash
cd backend
npm install
```

Create a `.env` file inside the backend directory:

```env
MONGO_URI=mongodb://localhost:27017/onlinejudge
JWT_SECRET=replace_with_a_secure_secret
PORT=5000
```

Replace the example JWT secret with a secure value appropriate for your environment.

If the repository contains a sample-problem seeding script, run it according to its implementation to populate initial problem data.

### 3. Configure the Compiler Service

Open a separate terminal:

```bash
cd CodeArena/Online-Judge-main/compiler
npm install
```

Create the compiler service's `.env` file if required by its configuration:

```env
PORT=3001
MONGO_URI=mongodb://localhost:27017/onlinejudge
```

Confirm which environment variables the compiler service actually reads before starting it.

### 4. Configure the Frontend

Open another terminal:

```bash
cd CodeArena/Online-Judge-main/frontend
npm install
```

Create a frontend `.env` file:

```env
VITE_API_URL=http://localhost:5000
VITE_AUTH_URL=http://localhost:5000
VITE_COMPILER_URL=http://localhost:3001
```

These URLs assume that the backend and compiler service use ports `5000` and `3001`, respectively.

### 5. Start the Services

Start each service in its own terminal.

**Backend**

```bash
cd CodeArena/Online-Judge-main/backend
npm start
```

**Compiler service**

```bash
cd CodeArena/Online-Judge-main/compiler
npm start
```

**Frontend**

```bash
cd CodeArena/Online-Judge-main/frontend
npm run dev
```

Use the scripts defined in each directory's `package.json` if the available commands differ.

### 6. Open the Application

When all three services are running on their configured local ports, open:

| Service | Default URL |
|---|---|
| Frontend | http://localhost:5173 |
| Backend | http://localhost:5000 |
| Compiler service | http://localhost:3001 |

The actual addresses may differ depending on your local configuration.

## How to Use CodeArena

### For Users

1. Register an account or sign in.
2. Explore the available programming problems.
3. Select a problem and review its statement.
4. Choose a supported programming language.
5. Write your solution in the integrated editor.
6. Run your code and review the execution output.
7. Submit your solution and inspect the resulting verdict.
8. Review your submission history and available performance statistics.

### For Administrators

1. Sign in with an account that has the required administrative permissions.
2. Create or update programming problems.
3. Configure the relevant test cases.
4. Manage users and access roles.
5. Review the available platform statistics.

Administrative operations depend on the permissions and endpoints implemented in the application.

## Security Considerations

Code execution platforms require particular care because submitted programs may be untrusted.

The application includes authentication-related functionality and a separate compiler service. For deployment beyond a local development environment, additional security controls should be verified, including:

- Process and filesystem isolation for submitted programs.
- Execution time and memory limits.
- Restrictions on network access and system calls.
- Protection against command injection and malicious input.
- Secure handling of authentication secrets.
- Appropriate rate limits and error handling.

A separate compiler service does not, by itself, guarantee secure sandboxing. Review the actual execution implementation before running untrusted submissions on a public server.

## Key Engineering Concepts

Building CodeArena brings together several practical software engineering concepts:

- **Full-stack development:** Connecting a React application with backend APIs and persistent storage.
- **API design:** Defining communication between the frontend and server-side components.
- **Authentication:** Managing sessions and protected operations through JWT-based authentication.
- **Database modeling:** Organizing users, problems, submissions, and test cases.
- **Code execution:** Coordinating language-specific compilation or interpretation and collecting execution results.
- **Problem evaluation:** Comparing program output against expected results.
- **Component-based architecture:** Separating application responsibilities into maintainable modules.
- **Error handling:** Managing invalid submissions, execution failures, and unexpected API responses.

## Future Enhancements

Potential areas for extending CodeArena include:

- Additional programming languages.
- More detailed submission analytics.
- Contest creation and timed programming rounds.
- Advanced leaderboard filtering.
- Stronger execution isolation and resource controls.
- Automated integration tests.
- Deployment automation and monitoring.
- Improved accessibility and editor customization.

These are potential extensions and should not be interpreted as features that are already implemented.

## Acknowledgment

CodeArena is developed as a programming and software engineering project focused on online judging, coding practice, and full-stack application development.

---

**Explore the repository:** [github.com/Pragati4566/CodeArena](https://github.com/Pragati4566/CodeArena)
