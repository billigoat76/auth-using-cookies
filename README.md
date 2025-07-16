# auth-using-cookies
🔐 Authentication system using HTTP cookies in Node.js — handles login, logout, sessions, and user access control without storing tokens in localStorage.

## 📖 What is Authentication?

Authentication is the process of letting users **sign up** or **sign in** to websites using:

- `username` / `password`
- or SSO (Single Sign-On)

<img width="2652" height="1626" alt="image" src="https://github.com/user-attachments/assets/49877168-fee4-479c-8b4c-65fa922a371d" />

## 🔑 Authentication using JWT + LocalStorage

Before diving deep into **authentication using cookies**, let’s understand the basic flow of:

> **JWT-based authentication stored in localStorage**

<img width="3260" height="1472" alt="image" src="https://github.com/user-attachments/assets/105d7084-0f63-4672-a452-185f9cf63174" />
<img width="3322" height="1440" alt="image" src="https://github.com/user-attachments/assets/abc258e8-a10e-45a7-bd36-fadaa2671a10" />
<img width="3384" height="1550" alt="image" src="https://github.com/user-attachments/assets/1a7f7a37-5f12-42ad-8f3c-58dd66127976" />

## 🍪 Authentication using Cookies (Part 1)

### 🔍 What are Cookies?

Cookies in web development are small pieces of data sent from a website and **stored in the user's browser**. They are similar in behavior to `localStorage`, but offer more control and features.

---

### 🍪 Use Cases of Cookies

1. **Session Management**  
   Store session info to track individual user states across multiple pages/visits.

2. **Personalization**  
   Save user preferences, interests, and show personalized content or ads.

3. **Tracking**  
   Enable user behavior tracking across pages or websites for analytics/ads.

4. **Security**  
   Secure cookies can:
   - Only be sent over HTTPS (`Secure` flag)
   - Be inaccessible to JavaScript (`HttpOnly` flag)
   - Help avoid XSS and session hijacking

📌 **➡️ We'll focus on Point 4: Security**

---

### ❓ Why Not Use Local Storage?

While `localStorage` can also store tokens or session data, cookies have key advantages — especially for secure authentication:

| Feature               | `localStorage`                  | Cookies                         |
|------------------------|----------------------------------|----------------------------------|
| Sent automatically?   | ❌ No (must add in headers)      | ✅ Yes (sent with every request) |
| Can expire?           | ✅ Yes (manually)               | ✅ Yes (via `expires` or `max-age`) |
| Secure (HTTPS only)?  | ❌ No                           | ✅ Yes (`Secure` flag)           |
| HttpOnly support?     | ❌ No (always accessible by JS) | ✅ Yes (`HttpOnly` = JS can't access) |
| Useful in Next.js?    | ⚠️ Some limitations            | ✅ Fully supported & flexible    |

---

### 🧠 Why This Matters for Next.js

In frameworks like **Next.js**, server-side rendering (SSR) plays a major role.  
Cookies shine here because:

- You **don’t need to manually attach tokens** on each request
- Cookies are **automatically available in SSR** via headers
- They provide **better security** using flags like `HttpOnly` and `Secure`
