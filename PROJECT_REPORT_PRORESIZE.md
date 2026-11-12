# PROJECT REPORT
## ProResize - Instant Photo Resize
### A Web-Based Image Resizing, Compression and Cropping Application

Submitted in partial fulfilment of the requirements for the degree of **B.Sc. IT**

Submitted by: **Abhinav Sarma (US-231-023-0083)**  
Under the guidance of: **Mr. Manjit Kr. Nath**  
Department of Information Technology  
Lalit Chandra Bharali College  
Academic Year: **2025-2026**

---

## Certificate
This is to certify that the project titled **"ProResize - Instant Photo Resize"** is a genuine work completed by **Abhinav Sarma (US-231-023-0083)** under my guidance.

This project report is submitted in partial fulfilment of the requirements for the degree of B.Sc. IT at Lalit Chandra Bharali College. The work presented in this report is original and has not been submitted to any other institution for any degree or diploma.

Supervisor Signature: ____________________  
Name: Mr. Manjit Kr. Nath  
Date: ____________________

---

## Declaration
I, **Abhinav Sarma (US-231-023-0083)**, hereby declare that the project report entitled **"ProResize - Instant Photo Resize"** is my original work carried out during the academic year 2025-2026 under the supervision of Mr. Manjit Kr. Nath.

I further declare that:
- This work has not been submitted previously for any degree or diploma.
- All references used are properly acknowledged.
- The implementation and documentation are completed by me, except where clearly stated.

Student Signature: ____________________  
Date: ____________________

---

## Acknowledgement
I express my sincere gratitude to **Mr. Manjit Kr. Nath** for his valuable guidance, encouragement, and support throughout this project.

I also thank the Head of Department and all faculty members of the Department of Information Technology, Lalit Chandra Bharali College, for their academic support. I am grateful to my friends and family for their constant motivation during the completion of this work.

---

## Abstract
ProResize is a browser-based image utility designed to simplify common image editing tasks such as compression, resizing, cropping, and format conversion without requiring heavyweight desktop software. The application focuses on speed, privacy, and ease of use by processing image operations directly in the browser using HTML5 Canvas and JavaScript.

The system supports multiple input formats (JPG, PNG, WebP, GIF, BMP, SVG, ICO) and provides two compression methods: quality-based compression and target file-size compression. It also includes custom width/height resizing with optional aspect-ratio locking, an interactive crop tool, social media dimension presets, and government exam form presets. Output files can be downloaded instantly in JPEG, PNG, or WebP format.

To improve user experience across devices, the interface is responsive and optimized for desktop and mobile screens. The project also integrates Firebase authentication and cloud-synced edit history metadata, while the actual image data remains local in the browser for better privacy.

This project demonstrates practical web development skills and client-side image processing techniques suitable for real-world productivity applications.

**Keywords:** Image Resizer, Image Compressor, Browser-based Editing, HTML5 Canvas, JavaScript, Firebase, Responsive Web App.

---

## Index
1. Introduction  
2. Literature Review  
3. System Analysis and Design  
4. Methodology and Implementation  
5. Working of the Project  
6. Testing  
7. Advantages and Limitations  
8. Future Improvements  
9. Appendix  
10. Conclusion  
11. References

---

## Chapter 1: Introduction
### 1.1 Introduction
In the current digital ecosystem, image files are used across social media, websites, online forms, e-commerce platforms, and educational portals. Different platforms require specific dimensions and file sizes. Many users struggle with traditional editing software because it is heavy, complex, or paid.

ProResize solves this by offering a lightweight web application that performs image optimization tasks instantly in the browser. Users can upload an image, apply compression or resize rules, preview the result, and download the processed output within seconds.

### 1.2 Problem Statement
Users often face the following challenges:
- Existing tools are difficult for beginners.
- Many tools require installation and high system resources.
- Quick tasks like image resizing still involve multiple complex steps.
- Mobile-friendly image editing options are limited.
- Job and exam form uploads fail due to strict size or dimension requirements.

### 1.3 Objectives
- To develop an easy and efficient browser-based image utility.
- To provide quick image compression and resizing with minimal steps.
- To support custom dimensions and output formats.
- To include preset-based workflows for social media and exam forms.
- To provide responsive design for desktop and mobile devices.
- To maintain privacy by local client-side image processing.
- To add optional account-based history sync for user convenience.

### 1.4 Scope of the Project
The project is intended for students, job applicants, social media creators, and general users. It supports:
- Online form photo/signature preparation
- Social media image sizing
- Basic image optimization for websites
- Fast file-size reduction before upload

Future scope includes batch processing, drag-reorder workflows, cloud backup of outputs, and AI-based smart resize suggestions.

---

## Chapter 2: Literature Review
### 2.1 Existing System
Existing image tools fall into three categories:
- Professional desktop software (feature-rich but complex and heavy)
- Basic online tools (simple but often ad-heavy or restrictive)
- Mobile apps (quick but less precise for technical dimension constraints)

### 2.2 Need for Proposed System
A focused web application is needed that combines:
- Simplicity of online tools
- Accuracy of technical dimension control
- Privacy of local processing
- Context-specific presets for real-world use cases

### 2.3 Review Summary
Based on comparative analysis, the gap exists in tools that are both beginner-friendly and technically practical for tasks like exam form photo preparation, exact target-size optimization, and one-click social-media presets. ProResize is designed to address this gap.

---

## Chapter 3: System Analysis and Design
### 3.1 Major Features
- Image upload via file picker and drag-drop
- File validation by type and max size (20 MB)
- Compression with:
  - Quality slider mode
  - Target size mode (KB/MB)
- Resize by width/height with lock-aspect option
- Crop module with draggable crop box, aspect presets, quick nudges
- Preset engine:
  - Government exam presets
  - Social media presets
- Output download in JPEG/PNG/WebP
- Preview modal for original/output images
- Theme handling and responsive UI
- Optional login and history tracking via Firebase

### 3.2 System Requirements
**Hardware:**
- Any modern desktop/laptop/mobile device
- Minimum 4 GB RAM recommended

**Software:**
- Web browser: Chrome, Edge, Firefox, Safari (latest versions)
- Frontend stack: HTML5, CSS3, JavaScript (ES6+)
- Backend services (optional): Firebase Authentication, Firestore/Realtime DB
- Hosting: static hosting platform (e.g., Vercel/Firebase Hosting)

### 3.3 System Architecture
ProResize follows a client-centric architecture:
- Presentation Layer: HTML + CSS responsive UI
- Processing Layer: JavaScript + Canvas APIs for image operations
- Persistence Layer:
  - LocalStorage for local preferences/history fallback
  - Firebase for authenticated history sync

### 3.4 Context Diagram (Textual)
- **Input Entity:** User uploads image and selects operations.
- **System:** ProResize processes image in browser.
- **Output Entity:** User receives processed downloadable file and optional history entry.
- **External Service:** Firebase handles authentication and metadata sync.

### 3.5 Level-1 DFD (Textual)
1. User provides image and options  
2. Validation module checks file type/size  
3. Selected processing module executes:
   - Compression / Resize / Crop / Preset flow  
4. Output generator builds final Blob URL  
5. Download module serves output file  
6. History module stores metadata locally/cloud

### 3.6 Data Model (Simplified)
**User**
- uid
- email
- displayName

**History Entry**
- clientHistoryId
- tool
- summary
- inputName
- inputSize
- outputSize
- dimensions
- format
- mode
- changeSummary
- createdAt

---

## Chapter 4: Methodology and Implementation
### 4.1 Methodology
An incremental approach was followed:
1. Requirement collection
2. UI wireframe and workflow design
3. Core processing implementation
4. Preset and productivity feature integration
5. Authentication and history integration
6. Testing and refinement

### 4.2 HTML Implementation
The interface is organized into tab-based modules:
- Compress
- Resize
- Presets
- Social presets
- Crop modal and preview modal
- Auth/history pages and navigation

### 4.3 CSS Implementation
Styles are implemented with:
- CSS variables for theming
- Responsive card/grid layouts
- Consistent button and input systems
- Modal and state-driven visual feedback

### 4.4 JavaScript Implementation
Core implementation uses:
- FileReader for loading local files
- Canvas APIs for resize/crop/draw/encode operations
- Blob generation and object URLs for downloadable outputs
- Binary search technique for target-size compression
- Dynamic rendering for preset cards and filters
- Accessibility behaviors for dialogs and keyboard actions

### 4.5 Firebase and Deployment
- Firebase Authentication supports login flow
- Firestore/Realtime DB stores edit history metadata
- Local fallback queue handles sync interruptions
- Application can be deployed as static files on Vercel/Firebase Hosting

---

## Chapter 5: Working of the Project
### 5.1 Image Upload Module
User uploads an image through browse or drag-drop. The system validates file type and size before processing.

### 5.2 Compression Module
Two modes are provided:
- **Quality Mode:** User picks quality level.
- **Target Mode:** User enters desired file size and system finds nearest quality automatically.

### 5.3 Resize Module
User enters width/height and can lock aspect ratio. Output is generated in selected format with updated dimensions.

### 5.4 Crop Module
Interactive crop area with handles, quick crop presets (full/square/portrait/story), ratio lock, and apply/reset actions.

### 5.5 Preset and Social Module
- Exam presets auto-fill format, dimensions, and size constraints.
- Social presets provide platform-specific recommended dimensions.
- One-click apply gives instant compliant outputs.

### 5.6 Download and History Module
Processed image is downloaded via generated file link. If user is logged in, operation metadata is saved to account history.

---

## Chapter 6: Testing
### 6.1 Functional Testing
- Upload valid image: Pass
- Reject unsupported format: Pass
- Compress output generation: Pass
- Resize output generation: Pass
- Crop apply and undo: Pass
- Preset apply and download: Pass
- Social preset apply and download: Pass

### 6.2 Responsive Testing
- Desktop layout: Pass
- Tablet layout: Pass
- Mobile layout: Pass
- Modal visibility and touch interactions: Pass

### 6.3 Performance Testing
- Local processing avoids server delay for most operations
- Medium-sized images process within acceptable user interaction time
- Object URL cleanup reduces memory leakage risk

### 6.4 Security and Privacy Considerations
- Raw image files are processed locally in browser
- Only lightweight operation metadata is stored when history sync is enabled
- Access control for cloud data handled through Firebase rules

---

## Chapter 7: Advantages and Limitations
### 7.1 Advantages
- No installation required
- Fast and user-friendly workflow
- Useful presets for practical real-world use
- Local image processing supports privacy
- Works across modern devices and browsers
- Optional account sync adds continuity

### 7.2 Limitations
- No multi-file batch processing in current version
- Very large images may consume higher client memory
- Internet needed for login/sync features
- Advanced editing (layers, filters) is not included

---

## Chapter 8: Future Improvements
### 8.1 Technical Enhancements
- Batch upload and batch export
- Progressively optimized background workers
- Undo/redo stack across all operations
- Better handling for animated formats

### 8.2 Feature Enhancements
- AI-driven auto-enhancement and smart crop suggestions
- OCR-assisted document crop modes
- More export presets (passport standards by country)
- PWA offline install support

### 8.3 Platform Extensions
- Browser extension release
- Dedicated mobile app wrapper
- Optional secure cloud output backup

---

## Chapter 9: Appendix
### 9.1 Suggested Screenshots to Attach
- Homepage
- Upload and preview section
- Compression panel with result
- Resize panel with result
- Crop modal interface
- Preset grid and applied preset result
- Social preset result
- Login/history interface
- Mobile responsive view

### 9.2 Sample Test Inputs
- JPG portrait photo (2-5 MB)
- PNG logo with transparency
- WebP social media image
- Exam-form photo and signature files

---

## Chapter 10: Conclusion
ProResize successfully achieves the objective of providing a fast, simple, and practical browser-based image utility for everyday users. It combines essential image operations with workflow-focused presets, responsive design, and optional history sync to deliver an application that is both technically useful and user-friendly.

The project demonstrates strong application of frontend engineering concepts, client-side media processing, and cloud-assisted user features. With future improvements such as batch processing and AI-assisted operations, ProResize can evolve into a complete lightweight image productivity platform.

---

## Chapter 11: References
1. MDN Web Docs - HTML Canvas API  
2. MDN Web Docs - FileReader API  
3. MDN Web Docs - Blob and URL APIs  
4. Firebase Documentation - Authentication  
5. Firebase Documentation - Firestore and Security Rules  
6. W3C HTML5 and CSS Standards  
7. Project source files: `index.html`, `script.js`, `styles.css`, `auth.js`, `firebase-config.js`

