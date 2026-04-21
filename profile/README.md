<div align="center">
  <table border="1">
    <tr>
      <td align="center" style="padding: 20px;">
        <h3>📢 Domain & Email Migration Notice</h3>
        <p>Since <b>19 March 2026</b>, Carbonhub has transitioned to new domains as <code>carbonhub.app</code> was not renewed:</p>
        <p>🌐 <b>Website:</b> <a href="https://carbonhub.faizath.com">carbonhub.faizath.com</a> (formerly <i>carbonhub.app</i>)<br>
        ⚙️ <b>API:</b> <a href="https://carbonhub-api.faizath.com">carbonhub-api.faizath.com</a> (formerly <i>api.carbonhub.app</i>)<br>
        🛰️ <b>CDN:</b> <a>carbonhub-cdn.faizath.com</a> (formerly <i>cdn.carbonhub.app</i>)<br>
        📧 <b>Email:</b> <code>contact@carbonhub.faizath.com</code> (formerly <i>contact@carbonhub.app</i>)</p>
      </td>
    </tr>
  </table>
</div>

# CarbonHub 🌱

CarbonHub is a comprehensive carbon credit trading and monitoring platform that combines blockchain technology, IoT sensors, and modern web/mobile applications to create a sustainable ecosystem for carbon credit management.

## 🌟 Project Overview

CarbonHub consists of four main components, each serving a specific purpose in the ecosystem:

### 1. CarbonHub Core (`carbonhub-core`) 🏗️

The backbone of the platform, providing the core API and blockchain integration.

**Repository:** [github.com/carbonhub-app/carbonhub-core](https://github.com/carbonhub-app/carbonhub-core)  
**Deployment:** [carbonhub-api.faizath.com](https://carbonhub-api.faizath.com)

**Key Features:**
- Decentralized carbon credit trading
- Real-time emissions tracking
- Token swaps between ECFCH and EURCH
- Secure authentication using Solana wallet signatures
- Carbon quota management
- Market data integration

**Tech Stack:**
- Backend: Node.js with Express.js
- Blockchain: Solana
- Token Standards: SPL Token
- Database: MongoDB
- Authentication: JWT with Solana wallet signatures
- API Documentation: OpenAPI 3.0
- Market Data: Yahoo Finance API
- Charting: TradingView Charts Embed

### 2. CarbonHub Frontend (`carbonhub-fe`) 🎨

A modern web application for users to interact with the CarbonHub platform.

**Repository:** [github.com/carbonhub-app/carbonhub-fe](https://github.com/carbonhub-app/carbonhub-fe)  
**Deployment:** [carbonhub.faizath.com](https://carbonhub.faizath.com)

**Key Features:**
- Modern and responsive user interface
- Real-time carbon credit trading
- Interactive charts and data visualization
- Dark/Light theme support
- Form validation and handling
- Toast notifications
- Beautiful animations

**Tech Stack:**
- Framework: Next.js 15.3.2
- Language: TypeScript
- UI Library: React 19
- Styling: TailwindCSS
- UI Components: Radix UI
- Icons: Lucide React
- Animations: Framer Motion, GSAP
- Data Visualization: Recharts
- Form Handling: React Hook Form
- Validation: Zod
- Blockchain: Solana Web3.js, Wallet Adapter

### 3. CarbonHub AIoT (`carbonhub-aiot`) 🤖

An intelligent IoT system for monitoring and detecting anomalies in CO₂ emissions.

**Repository:** [github.com/carbonhub-app/carbonhub-aiot](https://github.com/carbonhub-app/carbonhub-aiot)

**Key Features:**
- Real-time CO₂ monitoring
- AI-powered anomaly detection
- Dual-endpoint reporting
- Moving average filtering
- Statistical analysis

**Tech Stack:**
- Hardware: ESP32, MQ135 sensor
- Programming: Python
- Machine Learning: scikit-learn
- Data Processing: NumPy, SciPy
- Serial Communication: PySerial
- HTTP Client: Requests

### 4. CarbonHub Mobile (`carbonhub-mobile`) 📱

A cross-platform mobile application for on-the-go carbon footprint management.

**Repository:** [github.com/carbonhub-app/carbonhub-mobile](https://github.com/carbonhub-app/carbonhub-mobile)

**Key Features:**
- Modern and intuitive user interface
- Dark mode support
- Responsive design
- Cross-platform compatibility

**Tech Stack:**
- Framework: React Native with Expo
- Language: TypeScript
- UI Library: Gluestack UI
- Styling: NativeWind (Tailwind CSS)
- Navigation: Expo Router
- Storage: AsyncStorage
- Animations: React Native Reanimated
- Gestures: React Native Gesture Handler
- Icons: Expo Vector Icons

## 🚀 Getting Started

Each component has its own repository with detailed setup instructions. Please refer to the individual README files in each repository for specific setup and development guidelines.

## 📧 Contact

For any inquiries, please contact the CarbonHub development team at dev@carbonhub.faizath.com
