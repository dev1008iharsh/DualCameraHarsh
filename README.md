<h1 align="center">🎥 Advanced Camera System — Doctor Patient Recording App</h1>

<p align="center">
Production-grade iOS camera solution built using AVFoundation with secure medical data handling.
</p>

<p align="center">
<a href="https://youtu.be/7cVl1fcF2Tc">▶️ Watch Advanced Camera System Demo</a>
</p>

---

<h2>📸 Preview</h2>

<p align="center">
<img src="https://github.com/user-attachments/assets/71dd00cd-b4ca-4392-8502-0238018fecb6" width="70%" />
</p>

---

<h2>✨ Features</h2>

<ul>
<li>🎥 Dual Camera Capture (Front + Rear simultaneously)</li>
<li>📷 Single Camera Recording using AVCaptureSession</li>
<li>🎬 4K 60fps high-quality video recording</li>
<li>⚡ Real-time frame processing (CMSampleBuffer)</li>
<li>🎤 Independent audio recording pipeline</li>
<li>🔐 Password-protected ZIP compression before upload</li>
<li>☁️ Secure upload to Firebase Storage</li>
<li>🔄 Background upload with resume support</li>
<li>🔐 Google Sign-In authentication</li>
<li>📍 Sensor data collection (GPS, Motion, Altitude, Steps)</li>
<li>🧵 Thread-safe architecture using GCD + Swift Concurrency</li>
<li>🧠 Optimized memory management (ARC, weak references)</li>
<li>🏥 Designed for Doctor-Patient remote diagnostics use case</li>
</ul>

---

<h2>🎯 Key Highlights</h2>

<p>
Built a highly scalable and production-ready camera system that enables secure video recording 
and transmission for medical support scenarios where patients can record and send diagnostic videos to doctors.
</p>

---

<h2>📷 Camera Capabilities</h2>

<h3>🎥 Dual Camera System</h3>

<ul>
<li>Implemented using <b>AVCaptureMultiCamSession</b></li>
<li>Simultaneous front & rear capture</li>
<li>Picture-in-Picture rendering using <b>AVCaptureVideoPreviewLayer</b></li>
<li>Fallback using <b>ReplayKit (RPScreenRecorder)</b> for stability</li>
</ul>

---

<h3>📷 Single Camera Capture</h3>

<ul>
<li>Built using <b>AVCaptureSession</b> (core capture pipeline)</li>
<li>Camera accessed via <b>AVCaptureDevice</b></li>
<li>Input configured using <b>AVCaptureDeviceInput</b></li>
<li>Outputs:
  <ul>
    <li><b>AVCaptureVideoDataOutput</b></li>
    <li><b>AVCaptureAudioDataOutput</b></li>
  </ul>
</li>
<li>Live preview using <b>AVCaptureVideoPreviewLayer</b></li>
</ul>

<p>
👉 <b>Core Concept:</b> AVCaptureSession acts as the central pipeline that connects camera input to output streams and manages data flow efficiently  [oai_citation:0‡Apple Developer](https://developer.apple.com/documentation/avfoundation/avcapturesession?utm_source=chatgpt.com)
</p>

---

<h2>⚡ Real-Time Processing</h2>

<ul>
<li>Frame handling via <b>CMSampleBuffer</b></li>
<li>Delegate: <b>AVCaptureVideoDataOutputSampleBufferDelegate</b></li>
<li>Supports live processing (filters, transformations, analytics)</li>
</ul>

---

<h2>🎬 Video Encoding Pipeline</h2>

<ul>
<li><b>AVAssetWriter</b> for custom encoding</li>
<li><b>AVAssetWriterInput</b> for stream handling</li>
<li><b>PixelBufferAdaptor</b> for frame-level control</li>
<li>Optimized compression for reduced file size</li>
</ul>

---

<h2>🎤 Audio System</h2>

<ul>
<li>Separate recording using <b>AVAudioRecorder</b></li>
<li>Improved audio clarity and synchronization</li>
</ul>

---

<h2>🔐 Secure Data Handling</h2>

<ul>
<li>Video compressed into password-protected ZIP</li>
<li>Encryption before network transmission</li>
<li>Ensures medical-grade data security</li>
</ul>

---

<h2>☁️ Background Upload System</h2>

<ul>
<li>Implemented using <b>URLSession background configuration</b></li>
<li>Upload continues when app is minimized</li>
<li>Resume upload on app relaunch</li>
<li>Retry mechanism for failed uploads</li>
</ul>

---

<h2>🔐 Authentication</h2>

<ul>
<li>Google Sign-In integration</li>
<li>Secure user identity management</li>
</ul>

---

<h2>📍 Sensor Integration</h2>

<ul>
<li><b>CoreLocation</b> → GPS tracking</li>
<li><b>CoreMotion</b> → accelerometer, gyroscope</li>
<li><b>CMAltimeter</b> → altitude & pressure</li>
<li><b>CMPedometer</b> → steps & movement</li>
</ul>

---

<h2>🧵 Thread Safety & Performance</h2>

<ul>
<li>Dedicated queues using <b>DispatchQueue</b></li>
<li>Heavy work offloaded from main thread</li>
<li>Modern concurrency:
  <ul>
    <li><b>async/await</b></li>
    <li><b>Task</b></li>
    <li><b>MainActor</b></li>
  </ul>
</li>
</ul>

---

<h2>🧠 Memory Management</h2>

<ul>
<li>ARC-based lifecycle management</li>
<li>Weak references to avoid retain cycles</li>
<li>Safe handling of delegates & closures</li>
<li>Efficient buffer reuse for performance optimization</li>
</ul>

---

<h2>🧩 Architecture</h2>

<ul>
<li><b>CameraManager</b> → Capture session handling</li>
<li><b>RecordingManager</b> → Encoding pipeline</li>
<li><b>SensorManager</b> → Motion + location</li>
<li><b>CompressionService</b> → ZIP encryption</li>
<li><b>UploadService</b> → Firebase upload</li>
</ul>

---

<h2>⚙️ How It Was Built</h2>

<p>
This system is built using <b>AVFoundation</b>, Apple’s core multimedia framework, where the central component 
<b>AVCaptureSession</b> manages the complete capture pipeline including camera input and video/audio outputs. 
The application uses both <b>AVCaptureMultiCamSession</b> for dual camera capture and standard 
<b>AVCaptureSession</b> for single camera workflows, ensuring compatibility across devices.
</p>

<p>
Real-time video frames are processed using <b>CMSampleBuffer</b> through delegate callbacks, 
and encoded using <b>AVAssetWriter</b> to create optimized video files. Audio is recorded separately 
to maintain clarity and synchronization.
</p>

<p>
Once recording is completed, the video is compressed into a password-protected ZIP file to ensure 
data security. The file is then uploaded to Firebase Storage using a resilient background upload system 
that supports pause, resume, and retry functionality even if the app is terminated.
</p>

<p>
Additionally, the system collects sensor data using CoreLocation and CoreMotion, allowing doctors 
to analyze environmental and movement context along with video data.
</p>

<p>
Thread safety is maintained using GCD and Swift Concurrency, ensuring all heavy operations like encoding 
and uploading are executed off the main thread, while UI updates remain responsive.
</p>

<p>
Memory is managed using ARC with best practices like weak references and controlled lifecycle handling 
to prevent leaks and crashes, making the system stable for long recording sessions.
</p>

---

<h2>👨‍💻 Author</h2>

<p>
<b>Harsh Darji — iOS Developer 🚀</b>
</p>

<ul>
<li><b>Developer:</b> Harsh</li>
<li><b>Role:</b> Senior iOS Engineer (Swift & UIKit Specialist)</li>
<li><b>Phone:</b> <a href="tel:+919662108047">+91 9662108047</a></li>
<li><b>Email:</b> <a href="mailto:dev.iharsh1008@gmail.com">dev.iharsh1008@gmail.com</a></li>
<li><b>GitHub:</b> <a href="https://github.com/dev1008iharsh">dev1008iharsh</a></li>
<li><b>LinkedIn:</b> <a href="https://www.linkedin.com/in/dev1008iharsh/">dev1008iharsh</a></li>
</ul>

---
