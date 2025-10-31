# JamboBites 🇰🇪☕

> **The most beautiful cafe experience in Kenya** - Order your favorite coffee and snacks with just a few taps.

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-5.2+-green.svg)](https://www.djangoproject.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue.svg)](https://www.typescriptlang.org/)
[![Nuxt](https://img.shields.io/badge/Nuxt-3.0+-00DC82.svg)](https://nuxt.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

---

## 🌟 What is JamboBites?

JamboBites is a modern, full-stack cafe management platform designed specifically for the Kenyan market. It brings together customers, cafe staff, and cafe owners in a seamless digital experience that celebrates Kenyan coffee culture.

### ✨ Key Features

- 🎨 **Beautiful UI/UX** - Built with DaisyUI and TailwindCSS for a stunning, modern interface
- 📱 **Multi-Platform** - Web (Nuxt.js), Mobile (Kotlin), and REST API (Django)
- 💰 **M-Pesa Integration** - Native support for Kenya's favorite payment method
- 🌍 **Kenyan Localization** - KES currency, Swahili language support, local business patterns
- ⚡ **Real-Time Updates** - Live order tracking and notifications
- 🔒 **Secure & Scalable** - JWT authentication, role-based access, production-ready architecture
- ♿ **Accessible** - WCAG 2.1 AA compliant, keyboard navigation, screen reader friendly
- 🌙 **Dark Mode** - Beautiful light and dark themes
- 📊 **Analytics Dashboard** - Business insights for cafe owners

---

## 🎯 For Everyone

### 👥 Customers

- Browse menus from multiple cafes
- Place orders with real-time tracking
- Pay securely with M-Pesa or card
- Save favorite items and cafes
- Get notifications when orders are ready

### 🧑‍🍳 Cafe Staff

- Receive orders instantly
- Update order status in real-time
- Manage menu availability
- Track daily sales and performance

### 👔 Cafe Owners

- Comprehensive dashboard with analytics
- Menu management and pricing
- Staff management
- Revenue tracking and insights
- Customer feedback monitoring

---

## 🏗️ Architecture

JamboBites is built as a modern, scalable monorepo with three main components:

```
JamboBites/
├── backend/          # Django REST API (Python 3.11+)
├── frontend/         # Nuxt.js Web App (TypeScript, Vue 3)
└── mobile/          # Kotlin Android App (coming soon)
```

### Technology Stack

#### Backend

- **Framework**: Django 5.2+ with Django REST Framework
- **Database**: PostgreSQL (production), SQLite (development)
- **Caching**: Redis
- **Authentication**: JWT tokens (access + refresh)
- **Payments**: M-Pesa API, Stripe
- **Task Queue**: Celery
- **Real-time**: Django Channels (WebSockets)

#### Frontend

- **Framework**: Nuxt 3 with TypeScript
- **UI Library**: DaisyUI + TailwindCSS
- **State Management**: Pinia
- **Icons**: Iconify (mdi, heroicons, lucide)
- **Image Optimization**: @nuxt/image
- **Testing**: Vitest
- **PWA**: Progressive Web App support

#### Mobile

- **Language**: Kotlin
- **UI**: Jetpack Compose + Material Design 3
- **Architecture**: MVVM with Hilt DI
- **Networking**: Retrofit + OkHttp
- **Local Storage**: Room Database
- **Testing**: JUnit 5 + Espresso

---

## 🚀 Quick Start

### Prerequisites

- **Backend**: Python 3.11+, PostgreSQL (optional), Redis (optional)
- **Frontend**: Node.js 20+, npm/yarn/pnpm
- **Mobile**: JDK 17+, Android Studio
- **Tools**: Git, Docker (optional)

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies (using uv for fast installs)
pip install uv
uv pip install -e .

# Run migrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Start development server
python manage.py runserver
```

The API will be available at `http://localhost:8000/api/`

### Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

The web app will be available at `http://localhost:3000`

### Mobile Setup

```bash
# Navigate to mobile directory
cd mobile

# Sync Gradle
./gradlew build

# Run on emulator or device
./gradlew installDebug
```

---

## 📖 Documentation

- [Backend API Documentation](backend/docs/API.md)
- [Frontend Development Guide](frontend/README.md)
- [Mobile Development Guide](mobile/README.md)
- [AI Agents Guide](agents.md) - For AI-assisted development
- [Deployment Guide](docs/DEPLOYMENT.md)
- [Contributing Guidelines](CONTRIBUTING.md)

---

## 🎨 Design System

JamboBites uses a custom DaisyUI theme inspired by Kenyan culture:

### Color Palette

- **Primary (Safari Sunset)**: `#f97316` - Warm, inviting orange
- **Secondary (Acacia Green)**: `#22c55e` - Fresh, natural green
- **Accent (Kilimanjaro Blue)**: `#3b82f6` - Cool, trustworthy blue

### Typography

- **Headings**: System fonts with Swahili character support
- **Body**: Clean, readable fonts optimized for mobile

### Components

All UI components follow the DaisyUI design system with custom Kenyan-inspired modifications. See [Design System Documentation](docs/DESIGN_SYSTEM.md) for details.

---

## 🧪 Testing

We maintain 80%+ test coverage across all platforms.

### Backend Tests

```bash
cd backend

# Run all tests
pytest

# Run with coverage
pytest --cov=apps --cov-report=html

# Run specific app tests
pytest apps/menu/tests/
```

### Frontend Tests

```bash
cd frontend

# Run all tests
npm run test

# Run with coverage
npm run test:coverage

# Run in watch mode
npm run test:watch
```

### Mobile Tests

```bash
cd mobile

# Run unit tests
./gradlew test

# Run instrumented tests
./gradlew connectedAndroidTest
```

---

## 🔧 Development Workflow

### Code Quality

We use automated tools to ensure code quality:

- **Backend**: Ruff (formatting & linting), mypy (type checking)
- **Frontend**: Prettier (formatting), ESLint (linting), TypeScript (type checking)
- **Mobile**: ktlint (formatting), detekt (linting)

### Pre-commit Hooks

```bash
# Install pre-commit
pip install pre-commit

# Install hooks
pre-commit install
```

This will automatically format and lint your code before each commit.

### Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(menu): add search functionality
fix(orders): resolve payment processing bug
docs(readme): update installation instructions
style(frontend): format code with prettier
refactor(api): improve error handling
test(backend): add menu item tests
chore(deps): update dependencies
```

---

## 🌍 Kenyan Localization

JamboBites is built with Kenya in mind:

- **Currency**: KES (Kenyan Shillings) - `KSh 500`
- **Phone Numbers**: +254 format with validation
- **Payments**: M-Pesa as primary payment method
- **Language**: English with Swahili phrases
- **Time Zone**: East Africa Time (UTC+3)
- **Business Hours**: Aligned with local patterns
- **Cultural Elements**: Subtle Kenyan design touches

---

## 📊 Performance

We prioritize performance across all platforms:

- **Web**: Core Web Vitals score > 90
- **API**: Response time < 200ms
- **Mobile**: Startup time < 2 seconds
- **Database**: Optimized queries with proper indexing
- **Caching**: Redis for frequently accessed data
- **CDN**: Static assets served via CDN

---

## 🔒 Security

Security is a top priority:

- ✅ JWT authentication with refresh tokens
- ✅ Role-based access control (RBAC)
- ✅ Rate limiting on all endpoints
- ✅ Input validation and sanitization
- ✅ HTTPS in production
- ✅ Secure password hashing (bcrypt)
- ✅ CORS policies
- ✅ CSRF protection
- ✅ Regular security audits

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Development Setup

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/amazing-feature`)
3. Make your changes
4. Run tests and linting
5. Commit your changes (`git commit -m 'feat: add amazing feature'`)
6. Push to the branch (`git push origin feat/amazing-feature`)
7. Open a Pull Request

### Code Review Process

All contributions go through code review to ensure:

- Code quality and consistency
- Test coverage
- Documentation updates
- Performance considerations
- Security best practices

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **DaisyUI** - For the beautiful component library
- **Nuxt Team** - For the amazing framework
- **Django Team** - For the robust backend framework
- **Kenyan Coffee Culture** - For the inspiration ☕

---

## 📞 Contact & Support

- **Website**: [jambobites.co.ke](https://jambobites.co.ke) (coming soon)
- **Email**: hello@jambobites.co.ke
- **Twitter**: [@jambobites](https://twitter.com/jambobites)
- **Issues**: [GitHub Issues](https://github.com/yourusername/JamboBites/issues)

---

## 🗺️ Roadmap

### Phase 1: MVP (Current)

- [x] Backend API foundation
- [x] Frontend web app
- [ ] Basic menu management
- [ ] Order placement and tracking
- [ ] M-Pesa integration
- [ ] User authentication

### Phase 2: Enhancement

- [ ] Mobile app (Kotlin)
- [ ] Real-time notifications
- [ ] Advanced analytics
- [ ] Multi-cafe support
- [ ] Staff management
- [ ] Loyalty program

### Phase 3: Scale

- [ ] Multi-city expansion
- [ ] Advanced recommendations
- [ ] Social features
- [ ] B2B partnerships
- [ ] API marketplace
- [ ] White-label solutions

---

## ⭐ Show Your Support

If you find JamboBites useful, please consider:

- Giving it a ⭐ on GitHub
- Sharing it with friends and colleagues
- Contributing to the project
- Reporting bugs and suggesting features

---

<div align="center">

**Made with ❤️ in Kenya 🇰🇪**

_Bringing the best of Kenyan cafe culture to your fingertips_

**[Get Started](#-quick-start)** • **[Documentation](#-documentation)** • **[Contributing](#-contributing)**

</div>
