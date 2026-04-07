# 🎥 Dual Camera Capture — Advanced iOS Camera System
Engineered an advanced iOS multi-camera system using AVFoundation and ReplayKit, enabling dual camera capture, real-time processing, 4K recording, secure compression and Firebase uploads, along with integrated sensor data tracking (CoreLocation &amp; CoreMotion) for a complete production-grade solution.

Youtube Video Link : https://youtu.be/7cVl1fcF2Tc

<img width="1127" height="615" alt="dualcamera" src="https://github.com/user-attachments/assets/9a634db7-2b00-4492-975c-5962120f9cfd" />


• 🎥 Built using AVFoundation, leveraging AVCaptureMultiCamSession for simultaneous front and rear camera capture with hardware-aware configuration
• 📷 Managed camera inputs using AVCaptureDevice and AVCaptureDeviceInput, with output streams via AVCaptureVideoDataOutput and AVCaptureAudioDataOutput for real-time processing
• 🖥️ Implemented hybrid dual-camera rendering using ReplayKit (RPScreenRecorder) to record composed UI (Picture-in-Picture via AVCaptureVideoPreviewLayer) for reliable dual-stream capture
• 🎬 Achieved 4K 60fps recording by configuring AVCaptureDevice.Format with optimized frame duration and resolution settings
• ⚡ Processed real-time frames using AVCaptureVideoDataOutputSampleBufferDelegate, handling CMSampleBuffer for live frame-level operations

• 📦 Built custom encoding pipeline using AVAssetWriter, AVAssetWriterInput, and AVAssetWriterInputPixelBufferAdaptor for efficient compression and optimized video output
• 🎤 Captured separate audio instructions using AVAudioRecorder, enabling independent audio stream management and synchronization flexibility

• 🔐 Implemented secure file packaging using ZIPFoundation / SSZipArchive for password-protected ZIP compression before upload
• ☁️ Integrated Firebase Storage (StorageReference) for secure file uploads, metadata handling, and progress monitoring

• 📍 Captured location data using CLLocationManager (CoreLocation) for GPS (latitude, longitude) tracking
• 📱 Collected motion data using CMMotionManager (CoreMotion) including accelerometer, gyroscope, magnetometer, and device motion (attitude, gravity, rotation rate)
• 🌡️ Measured altitude and pressure using CMAltimeter, and tracked steps/distance using CMPedometer

• 🧵 Ensured thread safety and performance using GCD (DispatchQueue) and Swift Concurrency (Task, MainActor) for background processing and UI updates
• 🧠 Applied ARC-based memory management, avoiding retain cycles using weak references in asynchronous and delegate-based workflows

• 🧩 Designed modular architecture with components like CameraManager, RecordingManager, SensorManager, CompressionService, and UploadService, following clean architecture and separation of concerns

<img width="1126" height="614" alt="dualcamera2" src="https://github.com/user-attachments/assets/e2f41892-7de0-4e90-b661-965c360e032a" />


This advanced iOS camera system is built using a combination of AVFoundation, ReplayKit, CoreMotion, CoreLocation, and Firebase SDKs, structured in a modular architecture to handle real-time video capture, processing, sensor fusion, and secure data transmission. The core of the camera pipeline is powered by AVFoundation, specifically AVCaptureMultiCamSession, which enables simultaneous access to both front and rear cameras. Camera hardware is accessed via AVCaptureDevice, and input streams are configured using AVCaptureDeviceInput, while output streams are handled through AVCaptureVideoDataOutput for real-time frame delivery and AVCaptureAudioDataOutput when capturing audio along with video.

Since iOS imposes hardware and performance constraints on true dual-camera recording, an alternative hybrid approach is implemented using ReplayKit’s RPScreenRecorder, which records the composed UI layer where both camera feeds are rendered (for example, using a Picture-in-Picture layout with AVCaptureVideoPreviewLayer). This approach ensures consistent recording of both streams even under device limitations. For achieving high-quality video output such as 4K at 60fps, the system configures camera capabilities using AVCaptureDevice.Format, adjusting frame durations and resolution to match supported hardware formats.

Real-time video processing is achieved through AVCaptureVideoDataOutputSampleBufferDelegate, where each CMSampleBuffer frame is intercepted and processed. These frames are then encoded and written to disk using AVAssetWriter, along with AVAssetWriterInput and AVAssetWriterInputPixelBufferAdaptor, forming a custom compression pipeline that ensures efficient encoding, reduced file size, and optimized storage. This also enables applying transformations, overlays, or frame-level optimizations if required.

Audio instructions are recorded independently using AVAudioRecorder, allowing better control over audio quality, synchronization, and post-processing. This separation ensures that instructional audio is cleanly captured without being affected by video processing overhead.

For secure packaging of recorded data, files are compressed into archives using libraries like ZIPFoundation or SSZipArchive, which support password-protected ZIP creation. This ensures that sensitive data is encrypted before being transmitted. The final compressed output is uploaded to cloud storage using Firebase Storage (Storage SDK), where StorageReference is used to manage file paths and uploads, along with metadata handling and progress tracking for reliability.

In parallel, the system captures rich environmental and motion data using CoreLocation and CoreMotion frameworks. CLLocationManager is used for GPS tracking (latitude and longitude), while CMMotionManager provides access to accelerometer, gyroscope, and magnetometer data. Advanced fused motion data is retrieved via device motion updates (attitude, gravity, rotation rate). Additional sensors include CMAltimeter for altitude and air pressure measurements, and CMPedometer for tracking steps, distance, and user movement patterns. This multi-sensor integration enables contextual awareness alongside video recording.

Threading and performance optimization are handled using Grand Central Dispatch (GCD) and Swift Concurrency (Task, MainActor), ensuring that heavy operations such as encoding, compression, and network uploads are executed on background queues, while UI updates remain on the main thread. Memory management is carefully handled using ARC with techniques like weak references to avoid retain cycles, especially in delegate-based and asynchronous operations.

Architecturally, the system is divided into multiple reusable and testable components such as a CameraManager (handling AVFoundation setup), RecordingManager (handling AVAssetWriter and file output), SensorManager (CoreMotion and CoreLocation data aggregation), CompressionService (ZIP handling), and UploadService (Firebase integration). This modular design follows principles of clean architecture and separation of concerns, making the system scalable, maintainable, and production-ready.

Overall, this solution demonstrates advanced expertise in real-time media processing, multi-camera handling, sensor fusion, secure data workflows, and performance optimization, making it suitable for complex applications such as telemedicine, surveillance, logistics tracking, or AI-assisted video analytics.


