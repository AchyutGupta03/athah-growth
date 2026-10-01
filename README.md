# Athah Growth

> A multi-service super-app digital ecosystem consolidating daily lifestyle, utility, and entertainment services into a single platform.

## 🎯 Vision

Athah Growth is a scalable web and mobile platform that brings together essential daily services—**payments**, **food & local commerce**, and **entertainment & streaming**—into one seamless, unified experience.

**Core Promise:** Access all your lifestyle needs without switching apps.

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Architecture](#-architecture)
- [Development Roadmap](#-development-roadmap)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### Financial & Utility Payments Hub
- Peer-to-peer (P2P) money transfers
- Bill and merchant payments
- Digital wallet with balance tracking
- Transaction history and detailed ledger
- Multiple payment method support (cards, UPI, bank accounts)
- Payment reconciliation and receipt management

### Food Delivery & Local Commerce
- Interactive restaurant and grocery store listings
- Advanced search and filtering (by rating, delivery time, price, cuisine, etc.)
- Real-time inventory and availability tracking
- Shopping cart with quantity management
- Checkout flow with saved addresses and payment methods
- Live order tracking with delivery status
- Order history and quick re-order

### Entertainment & Streaming Hub
- Video streaming with adaptive bitrate
- Audio player with playlist support
- Content discovery with trending, recommendations, and categories
- Watch history and continue-watching functionality
- Playlist creation and management
- Creator content and original shows

### Core Experience
- Unified Single Sign-On (SSO) with social login options
- Persistent user profiles across all services
- Global navigation hub for seamless module switching
- Responsive design for desktop, tablet, and mobile
- Progressive Web App (PWA) support for mobile web
- Personalized recommendations feed
- Real-time push notifications
- Dark and light theme support

---

## 🛠️ Tech Stack

### Frontend
- **Web App:** Next.js (React) with TypeScript
- **Mobile App:** React Native + Expo
- **Design System:** Storybook + shared component library
- **Styling:** Tailwind CSS + CSS Modules
- **State Management:** Redux Toolkit + Redux Thunk
- **HTTP Client:** Axios + TanStack React Query
- **Forms:** React Hook Form + Zod validation
- **Testing:** Jest + React Testing Library + Cypress

### Backend
- **Runtime:** Node.js
- **Framework:** NestJS with TypeScript
- **API:** REST + GraphQL (optional layer)
- **ORM:** TypeORM or Prisma
- **Validation:** class-validator + class-transformer
- **Testing:** Jest + Supertest
- **Logging:** Winston
- **Authentication:** JWT + Passport.js

### Database & Cache
- **Primary Database:** PostgreSQL 14+
- **Caching & Sessions:** Redis
- **Search Engine:** Elasticsearch/OpenSearch
- **Object Storage:** AWS S3 / MinIO
- **Queue:** Kafka or RabbitMQ

### Infrastructure & DevOps
- **Containerization:** Docker
- **Orchestration:** Kubernetes (or Docker Compose for dev)
- **Cloud Provider:** AWS / GCP / Azure
- **Infrastructure as Code:** Terraform
- **CI/CD:** GitHub Actions
- **Monitoring:** Prometheus + Grafana
- **Tracing:** OpenTelemetry + Jaeger
- **Log Aggregation:** ELK Stack or CloudWatch

### External Integrations
- **Payment Gateways:** Stripe, Razorpay, Local Gateway Abstraction
- **Maps & Geolocation:** Google Maps API / Mapbox
- **Media Streaming:** Cloudflare Stream / AWS CloudFront
- **Notifications:** Firebase Cloud Messaging (FCM), Twilio, SendGrid
- **Analytics:** Mixpanel, Segment, or Custom Events

---

## 📁 Project Structure

```text
athah-growth/
├── apps/
│   ├── web/                          # Next.js web application
│   │   ├── src/
│   │   │   ├── pages/                # Route pages (App Router)
│   │   │   ├── components/           # Reusable React components
│   │   │   ├── hooks/                # Custom React hooks
│   │   │   ├── lib/                  # Utilities and helpers
│   │   │   ├── services/             # API client services
│   │   │   ├── store/                # Redux store and slices
│   │   │   ├── styles/               # Global styles
│   │   │   ├── types/                # TypeScript types and interfaces
│   │   │   └── __tests__/            # Unit and integration tests
│   │   ├── public/                   # Static assets
│   │   ├── next.config.js
│   │   ├── tailwind.config.js
│   │   ├── tsconfig.json
│   │   └── package.json
│   │
│   ├── mobile/                       # React Native + Expo app
│   │   ├── src/
│   │   │   ├── screens/              # Screen components
│   │   │   ├── components/           # Reusable components
│   │   │   ├── hooks/                # Custom React hooks
│   │   │   ├── navigation/           # React Navigation setup
│   │   │   ├── services/             # API client services
│   │   │   ├── store/                # Redux store and slices
│   │   │   ├── utils/                # Helper functions
│   │   │   ├── types/                # TypeScript types
│   │   │   └── __tests__/            # Tests
│   │   ├── app.json
│   │   ├── eas.json
│   │   ├── tsconfig.json
│   │   └── package.json
│   │
│   └── admin/                        # Admin dashboard (optional)
│       ├── src/
│       ├── public/
│       ├── package.json
│       └── tsconfig.json
│
├── packages/
│   ├── ui/                           # Shared design system & components
│   │   ├── src/
│   │   │   ├── components/           # Button, Card, Input, etc.
│   │   │   ├── icons/                # SVG icons
│   │   │   ├── theme/                # Theme configuration
│   │   │   ├── utils/                # Style utilities
│   │   │   └── index.ts
│   │   ├── storybook/
│   │   ├── package.json
│   │   └── tsconfig.json
│   │
│   ├── types/                        # Shared TypeScript types
│   │   ├── src/
│   │   │   ├── api/                  # API response/request types
│   │   │   ├── domain/               # Domain models
│   │   │   ├── entities/             # Entity types
│   │   │   └── index.ts
│   │   ├── package.json
│   │   └── tsconfig.json
│   │
│   ├── utils/                        # Shared utilities
│   │   ├── src/
│   │   │   ├── validators/
│   │   │   ├── formatters/
│   │   │   ├── helpers/
│   │   │   └── constants/
│   │   ├── package.json
│   │   └── tsconfig.json
│   │
│   └── api-client/                   # Shared API client SDK
│       ├── src/
│       │   ├── client/               # Axios/HTTP client setup
│       │   ├── auth/                 # Auth interceptors
│       │   ├── endpoints/            # API endpoint definitions
│       │   └── index.ts
│       ├── package.json
│       └── tsconfig.json
│
├── services/
│   ├── api/                          # NestJS backend API
│   │   ├── src/
│   │   │   ├── main.ts               # Entry point
│   │   │   ├── app.module.ts         # Root module
│   │   │   ├── config/               # Configuration (env, db, etc.)
│   │   │   │
│   │   │   ├── modules/
│   │   │   │   ├── auth/             # Authentication domain
│   │   │   │   │   ├── auth.module.ts
│   │   │   │   │   ├── auth.service.ts
│   │   │   │   │   ├── auth.controller.ts
│   │   │   │   │   ├── jwt.strategy.ts
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   ├── users/            # User profiles domain
│   │   │   │   │   ├── users.module.ts
│   │   │   │   │   ├── users.service.ts
│   │   │   │   │   ├── users.controller.ts
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   ├── payments/         # Payments & Wallet domain
│   │   │   │   │   ├── payments.module.ts
│   │   │   │   │   ├── payments.service.ts
│   │   │   │   │   ├── payments.controller.ts
│   │   │   │   │   ├── wallet/
│   │   │   │   │   ├── transactions/
│   │   │   │   │   ├── gateways/     # Payment gateway adapters
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   ├── commerce/         # Food & local commerce domain
│   │   │   │   │   ├── commerce.module.ts
│   │   │   │   │   ├── merchants/
│   │   │   │   │   ├── products/
│   │   │   │   │   ├── categories/
│   │   │   │   │   ├── search/
│   │   │   │   │   ├── carts/
│   │   │   │   │   ├── orders/
│   │   │   │   │   ├── delivery/
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   ├── media/            # Entertainment & streaming domain
│   │   │   │   │   ├── media.module.ts
│   │   │   │   │   ├── content/
│   │   │   │   │   ├── streaming/
│   │   │   │   │   ├── playlists/
│   │   │   │   │   ├── watch-history/
│   │   │   │   │   ├── recommendations/
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   ├── notifications/    # Notification service
│   │   │   │   │   ├── notifications.module.ts
│   │   │   │   │   ├── notifications.service.ts
│   │   │   │   │   ├── channels/     # Email, SMS, Push
│   │   │   │   │   ├── dtos/
│   │   │   │   │   ├── entities/
│   │   │   │   │   └── __tests__/
│   │   │   │   │
│   │   │   │   └── analytics/        # Analytics & events
│   │   │   │       ├── analytics.module.ts
│   │   │   │       ├── analytics.service.ts
│   │   │   │       ├── dtos/
│   │   │   │       ├── entities/
│   │   │   │       └── __tests__/
│   │   │   │
│   │   │   ├── common/               # Shared backend utilities
│   │   │   │   ├── decorators/
│   │   │   │   ├── filters/
│   │   │   │   ├── guards/
│   │   │   │   ├── interceptors/
│   │   │   │   ├── middleware/
│   │   │   │   ├── pipes/
│   │   │   │   └── utils/
│   │   │   │
│   │   │   ├── database/             # Database setup
│   │   │   │   ├── migrations/
│   │   │   │   ├── seeds/
│   │   │   │   └── database.module.ts
│   │   │   │
│   │   │   └── external/             # External integrations
│   │   │       ├── payment-gateways/
│   │   │       ├── maps-service/
│   │   │       ├── media-service/
│   │   │       ├── notification-service/
│   │   │       └── analytics-service/
│   │   │
│   │   ├── test/
│   │   ├── .env.example
│   │   ├── docker-compose.yml
│   │   ├── Dockerfile
│   │   ├── nest-cli.json
│   │   ├── package.json
│   │   ├── tsconfig.json
│   │   └── jest.config.js
│   │
│   └── workers/                      # Optional background job workers
│       ├── src/
│       │   ├── jobs/                 # Job definitions
│       │   │   ├── payment-reconciliation.job.ts
│       │   │   ├── order-status-update.job.ts
│       │   │   ├── notification-delivery.job.ts
│       │   │   └── recommendation-refresh.job.ts
│       │   ├── queues/               # Queue setup
│       │   └── main.ts
│       ├── Dockerfile
│       ├── package.json
│       └── tsconfig.json
│
├── infra/                            # Infrastructure as Code
│   ├── terraform/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   ├── vpc.tf
│   │   ├── rds.tf
│   │   ├── elasticache.tf
│   │   ├── s3.tf
│   │   ├── iam.tf
│   │   ├── environments/
│   │   │   ├── dev/
│   │   │   ├── staging/
│   │   │   └── prod/
│   │   └── modules/
│   │
│   ├── docker/
│   │   ├── Dockerfile.api
│   │   ├── Dockerfile.worker
│   │   └── docker-compose.yml
│   │
│   └── kubernetes/
│       ├── namespace.yaml
│       ├── configmaps/
│       ├── secrets/
│       ├── deployments/
│       ├── services/
│       ├── ingress.yaml
│       └── kustomization.yaml
│
├── .github/
│   ├── workflows/
│   │   ├── ci-api.yml
│   │   ├── ci-web.yml
│   │   ├── ci-mobile.yml
│   │   ├── deploy-api-dev.yml
│   │   ├── deploy-api-staging.yml
│   │   ├── deploy-api-prod.yml
│   │   ├── deploy-web-staging.yml
│   │   ├── deploy-web-prod.yml
│   │   └── security-scan.yml
│   │
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   └── documentation.md
│   │
│   └── PULL_REQUEST_TEMPLATE.md
│
├── docs/
│   ├── ARCHITECTURE.md               # System architecture & diagrams
│   ├── API.md                        # API documentation
│   ├── DATABASE_SCHEMA.md            # Database schema and ER diagrams
│   ├── DEVELOPMENT.md                # Development setup guide
│   ├── DEPLOYMENT.md                 # Deployment & DevOps guide
│   ├── CONTRIBUTING.md               # Contribution guidelines
│   ├── ROADMAP.md                    # Product & technical roadmap
│   ├── SECURITY.md                   # Security policies
│   ├── TESTING.md                    # Testing strategy
│   └── decisions/                    # Architecture Decision Records (ADRs)
│       ├── adr-0001-monolith-vs-microservices.md
│       ├── adr-0002-tech-stack-selection.md
│       └── ...
│
├── scripts/
│   ├── setup.sh                      # Local development setup
│   ├── migrate.sh                    # Database migration runner
│   ├── seed.sh                       # Database seeding
│   ├── lint.sh                       # Linting all services
│   ├── test.sh                       # Run tests
│   ├── build.sh                      # Build all services
│   └── docker-build.sh               # Docker image builds
│
├── .env.example                      # Environment variables template
├── .gitignore
├── .editorconfig
├── lerna.json                        # Monorepo configuration
├── package.json                      # Parent package
├── tsconfig.base.json
├── jest.config.js
├── .eslintrc.json
├── .prettierrc
├── LICENSE
└── README.md                         # This file
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ and **npm** or **yarn**
- **Docker** and **Docker Compose** (for local services)
- **PostgreSQL** 14+ (or use Docker)
- **Redis** (or use Docker)
- **Git**

### Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AchyutGupta03/athah-growth.git
   cd athah-growth
   ```

2. **Install dependencies:**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Setup environment variables:**
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your configuration
   ```

4. **Start local services (PostgreSQL, Redis, etc.):**
   ```bash
   docker-compose -f services/api/docker-compose.yml up -d
   ```

5. **Run database migrations:**
   ```bash
   npm run db:migrate
   ```

6. **Seed sample data (optional):**
   ```bash
   npm run db:seed
   ```

### Running Services

**Backend API:**
```bash
cd services/api
npm run start:dev
# API runs on http://localhost:3000
```

**Web App:**
```bash
cd apps/web
npm run dev
# Web app runs on http://localhost:3001
```

**Mobile App (Expo):**
```bash
cd apps/mobile
npm run start
# Follow prompts to run on simulator or physical device
```

### Running Tests

```bash
# Test all services
npm run test

# Test specific service
npm run test:api
npm run test:web

# With coverage
npm run test:coverage
```

### Linting & Formatting

```bash
# Run ESLint
npm run lint

# Fix linting issues
npm run lint:fix

# Format with Prettier
npm run format
```

---

## 🏛️ Architecture

### High-Level System Design

```text
┌─────────────────────────────────────────┐
│          Client Layer                   │
├──────────────┬──────────────┬───────────┤
│  Web App     │  Mobile App  │ Admin     │
│  (Next.js)   │  (React Nav) │ Dashboard │
└──────────────┴──────────────┴───────────┘
                    │
        ┌───────────┴───────────┐
        │   API Gateway         │
        │  (Authentication,     │
        │   Rate Limiting)      │
        └───────────┬───────────┘
                    │
┌───────────────────┴───────────────────┐
│       NestJS Backend Services         │
├──────┬──────┬──────┬──────┬──────────┤
│Auth  │Users │Pay   │Comm  │ Media    │
│      │      │ment  │erce  │          │
├──────┼──────┼──────┼──────┼──────────┤
│      Notifications & Analytics        │
└──────┬──────┬──────┬──────┬──────────┘
       │      │      │      │
┌──────┴──────┴──────┴──────┴──────────┐
│       Data & Cache Layer              │
├────────────┬────────────┬─────────────┤
│ PostgreSQL │   Redis    │ Elasticsearch
└────────────┴────────────┴─────────────┘
       │           │            │
┌──────┴───────────┴────────────┴────────┐
│   External Services & Integrations     │
├──────────────┬───────────┬──────┬──────┤
│ Payment Gate │Maps Service│ FCM  │ CDN  │
│ Stripe/Razor │ Mapbox    │Push  │Media │
└──────────────┴───────────┴──────┴──────┘
```

### Module Dependency Graph

```text
Auth Service
    ↓
├─→ Users Service
    ├─→ Payments Service
    │   ├─→ Notifications
    │   └─→ Analytics
    │
    ├─→ Commerce Service
    │   ├─→ Search (Elasticsearch)
    │   ├─→ Orders
    │   ├─→ Delivery
    │   ├─→ Notifications
    │   └─→ Analytics
    │
    └─→ Media Service
        ├─→ Recommendations
        ├─→ Watch History
        ├─→ Notifications
        └─→ Analytics
```

**See [ARCHITECTURE.md](./docs/ARCHITECTURE.md) for detailed diagrams and explanations.**

---

## 📊 Development Roadmap

### Phase 1: Foundation (Weeks 1–3)
- ✅ Project setup and monorepo structure
- ✅ Design system and shared components
- ✅ Auth service (JWT, SSO)
- ✅ User profiles and preferences
- ✅ Global navigation shell

### Phase 2: Payments & Utility (Weeks 4–8)
- ⏳ Wallet service
- ⏳ Payment gateway integration (Stripe/Razorpay)
- ⏳ Bill payment flow
- ⏳ Transaction history and ledger
- ⏳ Receipt generation

### Phase 3: Food & Commerce (Weeks 9–12)
- ⏳ Merchant and product catalogs
- ⏳ Search and filtering
- ⏳ Shopping cart
- ⏳ Checkout flow
- ⏳ Order management and tracking

### Phase 4: Entertainment (Weeks 13–16)
- ⏳ Media catalog and CDN setup
- ⏳ Streaming player (video & audio)
- ⏳ Watch history and playlists
- ⏳ Recommendation engine
- ⏳ Creator content support

### Phase 5: Launch & Hardening (Weeks 17–20)
- ⏳ Performance optimization
- ⏳ Security audit and compliance
- ⏳ Load testing and scaling
- ⏳ Monitoring and alerting
- ⏳ Public beta launch

**See [ROADMAP.md](./docs/ROADMAP.md) for detailed sprint-by-sprint breakdown.**

---

## 📚 Documentation

- **[ARCHITECTURE.md](./docs/ARCHITECTURE.md)** – System design, data flow, and deployment topology
- **[API.md](./docs/API.md)** – REST API endpoint documentation and examples
- **[DATABASE_SCHEMA.md](./docs/DATABASE_SCHEMA.md)** – Database ERD and schema details
- **[DEVELOPMENT.md](./docs/DEVELOPMENT.md)** – Local setup, debugging, and development workflow
- **[DEPLOYMENT.md](./docs/DEPLOYMENT.md)** – CI/CD, Kubernetes, Terraform, and production deployment
- **[CONTRIBUTING.md](./docs/CONTRIBUTING.md)** – Code style, PR process, and contributor guidelines
- **[SECURITY.md](./docs/SECURITY.md)** – Security policies, vulnerabilities, and compliance
- **[TESTING.md](./docs/TESTING.md)** – Testing strategy, unit tests, integration tests, and E2E tests
- **[decisions/](./docs/decisions/)** – Architecture Decision Records (ADRs)

---

## 🔒 Security

- JWT-based authentication with refresh tokens
- Payment PCI compliance via tokenization
- Rate limiting on all public endpoints
- CORS configuration for frontend origins
- SQL injection prevention via ORM and parameterized queries
- Environment-based secrets management
- Regular security audits and dependency scanning

See [SECURITY.md](./docs/SECURITY.md) for detailed security policies.

---

## 🤝 Contributing

We welcome contributions! Please read our [CONTRIBUTING.md](./docs/CONTRIBUTING.md) guide for:
- Code style and linting standards
- Commit message conventions
- Pull request process
- Issue templates
- Testing requirements

### Quick Start for Contributors

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes and write tests
4. Run linter and tests: `npm run lint && npm run test`
5. Commit with a clear message: `git commit -m "feat: add new feature"`
6. Push to your fork and open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** – see the [LICENSE](./LICENSE) file for details.

---

## 🙋 Support & Contact

- **Issues & Bugs:** Open an issue on [GitHub Issues](https://github.com/AchyutGupta03/athah-growth/issues)
- **Discussions:** Use [GitHub Discussions](https://github.com/AchyutGupta03/athah-growth/discussions)
- **Email:** [contact@athahgrowth.com](mailto:contact@athahgrowth.com) *(placeholder)*
- **Documentation:** [Wiki](https://github.com/AchyutGupta03/athah-growth/wiki)

---

## 🎉 Acknowledgments

- Built with ❤️ by the Athah Growth team
- Inspired by leading super-apps (Grab, WeChat, Gojek)
- Special thanks to our open-source dependencies

---

**Made with 💚 for a better connected world.**

**Start contributing:** ⭐ Star this repo if you find it useful!
