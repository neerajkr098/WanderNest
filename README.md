# 🌍 WanderNest — Vacation Rental & Accommodation Platform
## LinkedIn- https://www.linkedin.com/feed/update/urn:li:activity:7514933196749406208/
## Live - https://wandernest-omwa.onrender.com/listings
## 📸 Overview & Key Highlights
- **Live Interactive Maps:** Pinpoint listing locations accurately using Mapbox Geocoding.
- **Cloud Media Storage:** Direct image uploads with on-the-fly transformations powered by Cloudinary.
- **Secure Authentication & Ownership:** Role-based controls preventing unauthorized listing or review modifications.
- **Data Integrity:** Dual client- and server-side schema validations using Joi.
---
## 🛠️ Tech Stack & Technologies Used
### **Backend & Architecture**
- **Runtime Environment:** [Node.js](https://nodejs.org/)
- **Framework:** [Express.js](https://expressjs.com/) (MVC Architecture & RESTful API Routing)
- **Database:** [MongoDB Atlas](https://www.mongodb.com/atlas) with [Mongoose ODM](https://mongoosejs.com/)
- **Session Management:** `express-session` with `connect-mongo` for persistent database session storage
### **Frontend & Templating**
- **Templating Engine:** [EJS](https://ejs.co/) & [EJS-Mate](https://github.com/JacksonTian/ejs-mate) for reusable layouts, partials, and boilerplate components
- **Styling:** CSS3, Modern Responsive Design, Bootstrap
### **Cloud Services & External APIs**
- **Maps & Geolocation:** [@mapbox/mapbox-sdk](https://www.mapbox.com/) (Forward Geocoding & Interactive Map Rendering)
- **Cloud Storage:** [Cloudinary](https://cloudinary.com/) with `multer` & `multer-storage-cloudinary` for multi-part image uploads
### **Security & Validation**
- **Authentication:** [Passport.js](http://www.passportjs.org/) & `passport-local-mongoose` (PBKDF2 salted hashing)
- **Authorization:** Custom middleware verifying resource ownership for modifying listings and deleting reviews
- **Schema Validation:** [Joi](https://joi.dev/) for strict server-side validation schemas
- **Flash Notifications:** `connect-flash` for instant, non-persistent user alerts and messaging
---
## ✨ Features & Functionality
### 1. 🏡 Listing Management (CRUD)
- Hosts can create new listings with titles, descriptions, pricing, locations, and images.
- Full editing and deletion support with authorization safeguards.
- Form inputs sanitized and validated prior to database persistence.
### 2. 🗺️ Geocoding & Mapbox Integration
- Automatic forward geocoding converts address strings into geographic GeoJSON coordinates `[longitude, latitude]`.
- Interactive Mapbox GL displays an interactive pin indicating the exact property location on the details page.
### 3. ☁️ Cloud Media Uploads
- Direct image uploading via `Multer` connected to Cloudinary storage buckets.
- Dynamic Cloudinary image transformation URLs for optimized thumbnail rendering during edit states.
### 4. 🔐 Authentication & Access Control
- User registration and login flows with encrypted credentials.
- Protection against unauthorized modifications: only the host who created a listing can edit or delete it.
- Session persistence across page reloads using Mongo store.
### 5. ⭐ Review & Rating System
- Authenticated guests can submit 1-to-5 star ratings alongside written reviews.
- Nested sub-document relationships linking reviews directly to individual listings and author profiles.
- Review deletion restricted solely to the original author.
### 6. 🛡️ Resilient Error Handling
- Custom `ExpressError` class for centralized HTTP error handling (404, 500, etc.).
- Informative flash banners on success or error triggers (e.g., login status, unauthorized access attempts).
---
## 📂 Project Directory Structure
```text
WanderNest/
├── controllers/          # Request handlers & application logic (MVC Controllers)
│   ├── listings.js
│   ├── reviews.js
│   └── users.js
├── models/               # Mongoose data schemas & models
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── routes/               # Express RESTful modular routers
│   ├── listing.js
│   ├── review.js
│   └── user.js
├── views/                # EJS templates, layouts, and partials
│   ├── layouts/
│   │   └── boilerplate.ejs
│   ├── listings/
│   │   ├── index.ejs
│   │   ├── show.ejs
│   │   ├── new.ejs
│   │   └── edit.ejs
│   └── users/
├── public/               # Static assets (custom CSS, client-side JS)
│   ├── css/
│   └── js/
│       └── map.js
├── utils/                # Helper utilities (wrapAsync, ExpressError)
├── cloudConfig.js        # Cloudinary & Multer configuration
├── middleware.js         # Authentication, authorization & validation middleware
├── schema.js             # Joi validation schemas
├── app.js                # Server entry point & Express configuration
└── package.json          # Project dependencies & scripts
