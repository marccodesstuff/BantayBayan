# BantayBayan - Emergency Response & Flood Safety Mobile App

![Flutter](https://img.shields.io/badge/Flutter-3.10.0-blue?logo=flutter)
![Dart](https://img.shields.io/badge/Dart-3.0+-blue?logo=dart)
![License](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Android%20|%20iOS%20|%20Web-brightgreen)

<p align="center">
<img src="https://media.licdn.com/dms/image/v2/D562DAQERW6luJ-FzgQ/profile-treasury-image-shrink_800_800/B56ZtkUkSDG0AY-/0/1766914672827?e=1768035600&v=beta&t=f6rwxd_Vjf278DC1ee__smeYNykXqYJ8eW-NYPXC53g" />
</p>

*BantayBayan* is a comprehensive mobile application designed to assist communities in the Philippines during natural disasters, particularly floods and typhoons. The app provides real-time situational awareness, emergency guidance, and offline accessibility for critical safety information.

## 🎯 Key Features

### 🗺️ Interactive Map Integration
- *Real-time Flood Reporting*: Users can pin flood locations and report severity levels
- *Offline Map Support*: Download map tiles for offline access using SQLite caching
- *Situational Report Dashboard*: View active flood reports with color-coded risk levels
- *Multiple Map Layers*: Toggle between OpenStreetMap and cached tile providers

### 🤖 AI-Powered Features
- *Flood Risk Prediction*: ML-powered prediction of flood probability and depth using TFLite models
- *Smart Scenario Analysis*: Analyze flood scenarios and generate risk assessments
- *BantAI Bayan Chatbot*: AI assistant providing emergency response guidance

### 📚 Safety Handbook
- *Comprehensive Safety Tips*: Organized by disaster type and priority level
- *Interactive Checklist*: Track preparedness with completion metrics
- *Weather Information*: Real-time weather updates and alerts
- *First Aid Guidance*: Step-by-step emergency medical response

### 👤 User Management
- *Phone-Based Authentication*: Secure login using SMS verification via Appwrite
- *User Profiles*: Store and manage emergency contact information
- *Offline Persistence*: Access key information without internet connection

### 🚨 Emergency Features
- *SOS Button*: One-tap distress signal transmission
- *Location Sharing*: Automatically share coordinates with emergency responders
- *Notification System*: Receive alerts for nearby flood incidents

### 🌐 Offline Capabilities
- *Tile Caching*: Pre-download map tiles for areas of interest
- *Route Caching*: Store frequently used routes for offline navigation
- *Data Synchronization*: Auto-sync when connectivity is restored

## 📋 Project Structure

<p align="center">
<img src="https://github.com/user-attachments/assets/c43ecf7e-fb21-4dac-b128-8379b7a8a2ba" />
</p>

```text
lib/
├── main.dart                        # App entry point
├── core/
│   ├── constants/                   # App constants
│   └── theme/
│       ├── colors.dart              # Color scheme (light/dark modes)
│       ├── text_styles.dart         # Global text styling
│       ├── theme.dart               # Material theme configuration
│       └── theme_provider.dart      # Theme state management
├── models/
│   └── api_models.dart              # Data models (ReportModel, RouteResult, etc.)
├── screens/
│   ├── chat_screen.dart             # BantAI Chatbot interface
│   ├── handbook_screen.dart         # Safety tips and guidelines
│   ├── home_page.dart               # Main navigation hub
│   ├── login_screen.dart            # Authentication UI
│   ├── map_screen.dart              # Interactive map with routing
│   └── situation_screen.dart        # Flood reporting dashboard
├── services/
│   ├── api_service.dart             # Appwrite API integration
│   ├── auth_service.dart            # Authentication logic
│   ├── cached_tile_provider.dart    # Custom map tile provider
│   ├── ml_prediction_service.dart   # ML model inference
│   ├── offline_cache_service.dart   # SQLite caching for offline usage
│   ├── routing_service.dart         # Route calculation (OSRM)
│   └── scenario_service.dart        # Scenario simulation
├── utils/                           # Utility functions
└── widgets/
    ├── chat_message.dart            # Chat bubble components
    ├── predefined_question_chip.dart# Quick question buttons
    └── sos_confirmation_modal.dart  # SOS emergency dialog

assets/
├── .env                             # Environment configuration
└── ml_models/                       # TFLite model files
```
## 🚀 Getting Started
### Prerequisites
- Flutter SDK 3.10.0 or higher
- Dart 3.0 or higher
- Android Studio / Xcode (for mobile development)
- Appwrite server instance (for backend)
- OSRM server instance (for routing)

### Installation

1. *Clone the repository*
   
   git clone <repository-url>
   cd bantaybayan
   

2. *Install dependencies*
   
   flutter clean
   flutter pub get
   

3. *Configure environment variables*
   Create a .env file in the project root:
   
env
   APPWRITE_ENDPOINT=https://your-appwrite-server.com/v1
   APPWRITE_PROJECT_ID=your_project_id
   APPWRITE_API_KEY=your_api_key
   OSRM_BASE_URL=https://your-osrm-server.com
   WEATHER_API_KEY=your_weather_api_key
   

4. *Run the app*
   
   flutter run
   

## 📦 Core Dependencies

### UI & Design
- *google_fonts*: Typography management
- *provider*: State management

### Maps & Location
- *flutter_map*: OpenStreetMap integration
- *google_maps_flutter*: Google Maps support
- *latlong2*: Coordinate utilities
- *geolocator*: GPS and location services

### Data & Storage
- *sqflite*: Local SQLite database
- *shared_preferences*: Key-value storage
- *path_provider*: File system access

### Backend & Networking
- *appwrite*: Backend-as-a-service
- *http*: HTTP client
- *flutter_dotenv*: Environment configuration

### Machine Learning
- *tflite_flutter*: TensorFlow Lite inference

## 🔑 Key Services

### AuthService
Handles user authentication using Appwrite:
// Phone-based login
await authService.createPhoneSession(phoneNumber);
await authService.verifyPhoneCode(sessionId, code);

// User management
final user = authService.currentUser;
await authService.logout();

### ApiService
Manages API calls to Appwrite backend:
// Get flood reports
final reports = await ApiService.getReports();

// Submit new report
await ApiService.submitReport(reportData);

// Get weather data
final weather = await ApiService.getCurrentWeather(lat, lon);

### OfflineCacheService
Manages offline data persistence:
// Cache map tiles
await cacheService.cacheTilesForArea(center, radiusKm);

// Cache routes
await cacheService.cacheRoute(start, end, coordinates);

// Retrieve cached data
final cachedTiles = await cacheService.getCachedTiles(bounds);

### RoutingService
Calculates routes using OSRM:
// Find primary route
final route = await RoutingService.findRoute(start, destination);

// Find alternative routes
final routes = await RoutingService.findAlternativeRoutes(start, destination);

### MLPredictionService
Runs TensorFlow Lite models for flood prediction:
// Predict flood probability
final prediction = await MLPredictionService.predictFloodProbability(
  latitude, longitude, rainfall
);

## 📱 Screens Overview

| Screen | Purpose |
|--------|---------|
| *Login* | Phone-based authentication |
| *Home* | Navigation hub and quick actions |
| *Situation* | Active flood reports and map |
| *Map* | Detailed routing and navigation |
| *Checklist* | Compiled checklist of all essential items |
| *Handbook* | Safety tips and emergency guides |


## 🔒 Security Features

- *Phone Verification*: SMS-based identity verification
- *Appwrite Integration*: Secure backend authentication
- *Environment Variables*: Sensitive data in .env file
- *Offline Encryption*: Local data encryption for offline storage

## 📊 Data Models

### ReportModel
class ReportModel {
  final String id;
  final LatLng location;
  final String severity; // LOW, MODERATE, HIGH, VERY_HIGH
  final String description;
  final DateTime timestamp;
  final List<String> imageUrls;
}

### RouteResult
class RouteResult {
  final List<LatLng> coordinates;
  final double distanceKm;
  final double durationMinutes;
  final double averageFloodRisk;
  final List<RouteDirection> directions;
}

### WeatherModel
class WeatherModel {
  final double temperature;
  final int weatherCode;
  final double windSpeed;
  final double precipitation;
  final DateTime timestamp;
}

## 🌐 API Integration

### Appwrite
- User authentication and management
- Report storage and retrieval
- User preference storage
- Disaster alert notifications

### OSRM (Open Source Routing Machine)
- Route calculation
- Alternative route suggestions
- Turn-by-turn directions

### OpenWeatherMap (or similar)
- Current weather data
- Weather forecasts
- Severe weather alerts

## 📈 Performance Optimization

- *Lazy Loading*: Screens and data loaded on-demand
- *Caching*: Map tiles and routes cached locally
- *Image Optimization*: Compressed image uploads
- *Background Tasks*: Non-blocking network operations
- *Memory Management*: Proper disposal of controllers and listeners

## 🧪 Testing

To run tests:
flutter test

## 📝 Code Standards

- Follow Dart style guide
- Use meaningful variable and function names
- Comment complex logic
- Organize code into logical sections with fold markers
- Use Provider for state management

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit a pull request with a clear description

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Authors

- *Developer Team*: BantayBayan Development Team
- *Project*: HACKATHON - Baga Bugs Bantaybayan

## 🆘 Support & Reporting

For issues and feature requests, please use the GitHub issue tracker.

## 📞 Emergency Hotlines

*Important*: This app is a supplement to official emergency services.

*Emergency Numbers in the Philippines:*
- National Disaster Risk Reduction and Management Council (NDRRMC): 1-500-USAP
- Bureau of Fire Protection: 143
- Philippine National Police: 117
- Ambulance Services: 911

## 🔮 Future Roadmap

- [ ] Real-time satellite imagery integration
- [ ] Community crowdsourcing features
- [ ] Multi-language support
- [ ] Push notifications for nearby disasters
- [ ] Integration with government disaster systems
- [ ] Accessibility features (voice control, text-to-speech)
- [ ] Advanced analytics dashboard
- [ ] Video streaming of disaster areas

## 📚 Additional Resources

- [Flutter Documentation](https://flutter.dev/docs)
- [Appwrite Documentation](https://appwrite.io/docs)
- [OpenStreetMap](https://www.openstreetmap.org/)
- [OSRM Documentation](http://project-osrm.org/)

---

*BantayBayan*
Together, we build a safer Philippines through technology and community awareness.
