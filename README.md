# Vibe Coding Template

Welcome to the **Vibe Coding Template**. This repository is designed to structure modern software projects with comprehensive documentation and standardized testing practices.

## 📚 Documentation

The technical documentation is organized within the `.agent/documents/` directory to keep the root clean while providing deep insight for AI agents and developers.

### Quick Links

- **[📖 Documentation Home](.agent/documents/README.md)**: Central hub for all technical docs.
- **[📦 Modules](.agent/documents/application/modules/README.md)**: Feature specifications, Business Rules, and ERDs.
- **[🔌 API Specs](.agent/documents/application/api/README.md)**: REST API contracts and endpoint details.
- **[✅ Testing](.agent/documents/application/testing/README.md)**: Test scenarios (Positive, Negative, Monkey) and strategies.

## 🚀 Getting Started

1.  **Explore Modules**: Check `application/modules` to understand the domain business logic.
2.  **Review API**: Look at `application/api` for integration points.
3.  **Run Tests**: Follow the strategies in `application/testing`.

## 📁 Project Structure

```bash
.
├── .agent/
│   └── documents/          # Central Documentation Hub
│       ├── application/    # App-specific docs (API, Modules, Testing)
│       ├── templates/      # Standard templates for new docs
│       └── README.md       # Global Documentation Index
├── README.md               # You are here
└── [Source Code]           # Application source code (to be implemented)
```