# QAD-BOTDMSAF1-Resources

Shared resources library for BOT DMS (Debt Management System) Automation Framework - containing reusable keywords, libraries, and configurations for Robot Framework test automation.

## 📋 Overview

This repository contains the core resources for automating BOT DMS (Bank of Thailand - Debt Management System) testing, including:

- Custom Python libraries
- Reusable Robot Framework keywords
- Configuration files
- Database utilities
- Common helper functions

## 📁 Project Structure

```
qad-botdmsaf1-resources/
├── config/
│   ├── environments/
│   │   ├── dev.yaml
│   │   ├── uat.yaml
│   │   └── prod.yaml
│   └── database_config.yaml
├── libraries/
│   ├── __init__.py
│   ├── DatabaseLibrary.py
│   ├── ExcelLibrary.py
│   ├── DataProcessingLibrary.py
│   └── ReportingLibrary.py
├── keywords/
│   ├── common_keywords.resource
│   ├── database_keywords.resource
│   ├── file_keywords.resource
│   └── validation_keywords.resource
├── variables/
│   ├── global_variables.py
│   └── common_variables.resource
├── utils/
│   ├── __init__.py
│   ├── db_connector.py
│   ├── excel_handler.py
│   └── logger_config.py
├── data/
│   └── templates/
├── requirements.txt
├── setup.py
└── README.md
```

## 🔧 Installation

### Prerequisites

- Python 3.8+
- Oracle Instant Client (for database connectivity)
- Git

### Setup

1. Clone the repository:
```bash
git clone https://gitlab.bot.or.th/qad/qad-botdmsaf1-resources.git
cd qad-botdmsaf1-resources
```

2. Create and activate virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Install as editable package (for development):
```bash
pip install -e .
```

## 📦 Dependencies

```
robotframework>=6.0
robotframework-databaselibrary>=1.4
cx_Oracle>=8.3
openpyxl>=3.1.0
pandas>=2.0.0
PyYAML>=6.0
python-dotenv>=1.0.0
```

## 🔑 Available Keywords

### Database Keywords
| Keyword | Description |
|---------|-------------|
| `Connect To DMS Database` | Establish connection to DMS Oracle database |
| `Execute DMS Query` | Execute SQL query and return results |
| `Validate Record Count` | Validate expected vs actual record count |

### File Keywords
| Keyword | Description |
|---------|-------------|
| `Read Excel Data` | Read data from Excel file |
| `Generate Pivot Table` | Create pivot table from dataset |
| `Export To Excel` | Export data to Excel file |

### Validation Keywords
| Keyword | Description |
|---------|-------------|
| `Compare Datasets` | Compare two datasets for reconciliation |
| `Validate Data Format` | Validate data against expected format |
| `Calculate Variance` | Calculate variance between values |

## ⚙️ Configuration

### Environment Configuration

Create environment-specific YAML files in `config/environments/`:

```yaml
# dev.yaml
database:
  host: dev-db-server.bot.or.th
  port: 1521
  service_name: DMSDEV
  
paths:
  input_path: /data/input/dev/
  output_path: /data/output/dev/
  
logging:
  level: DEBUG
```

### Database Configuration

Configure database connections in `config/database_config.yaml`:

```yaml
dms_database:
  dialect: oracle
  driver: cx_oracle
  encoding: UTF-8
```

## 🔗 Usage in Test Cases

Add this repository as a dependency in your test case project:

```robot
*** Settings ***
Library    botdmsaf1_resources.libraries.DatabaseLibrary
Library    botdmsaf1_resources.libraries.ExcelLibrary
Resource   botdmsaf1_resources/keywords/common_keywords.resource
```

## 🧪 Testing

Run unit tests for libraries:
```bash
python -m pytest tests/ -v
```

## 📝 Contributing

1. Create a feature branch from `develop`
2. Make your changes
3. Write/update tests
4. Submit a merge request

### Branch Naming Convention
- Feature: `feature/BOTDMS-XXX-description`
- Bugfix: `bugfix/BOTDMS-XXX-description`
- Hotfix: `hotfix/BOTDMS-XXX-description`

## 📄 License

Internal use only - Bank of Thailand

## 👥 Contact

- **Team**: QAD Automation Team
- **Email**: qad-automation@bot.or.th
