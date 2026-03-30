# HelpCare System

A comprehensive blockchain-based healthcare platform built with Hyperledger Fabric for secure patient data management, medical records, and care coordination with privacy-preserving mechanisms.

## Overview

HelpCare System is an enterprise-grade solution designed to revolutionize healthcare data management through distributed ledger technology. It provides a secure, transparent, and interoperable system for managing patient records, medical histories, and care coordination while maintaining strict privacy standards.

## Key Features

- **Immutable Medical Records**: Blockchain-based storage ensures medical records cannot be altered retroactively
- **Privacy-Preserving Access Control**: Role-based access control with attribute-based encryption
- **Patient Consent Management**: Granular control over who accesses patient data and when
- **Interoperability**: Seamless data exchange between healthcare providers
- **Real-time Notifications**: Alert system for critical health events
- **Audit Trail**: Complete transaction history for compliance and verification
- **Multi-Party Transactions**: Smart contracts for coordinating care between providers

## Architecture

### Components

```
HelpCare System Architecture:

┌─────────────────────────────────────────────────────┐
│         Client Applications (Web/Mobile)            │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│           API Gateway & Load Balancer               │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│    Hyperledger Fabric Network (Permissioned)        │
│                                                      │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐    │
│  │  Hospital  │  │  Provider  │  │ Pharmacy   │    │
│  │   Orgs     │  │  Orgs      │  │   Orgs     │    │
│  └────────────┘  └────────────┘  └────────────┘    │
│                                                      │
│  Chaincode (Smart Contracts):                        │
│  - PatientRecordsCC                                 │
│  - AppointmentCC                                    │
│  - PrescriptionCC                                   │
│  - ConsentCC                                        │
└──────────────────┬──────────────────────────────────┘
                   │
┌──────────────────▼──────────────────────────────────┐
│    Distributed Ledger & World State Database         │
│         (CouchDB/LevelDB)                           │
└──────────────────────────────────────────────────────┘
```

## Technology Stack

- **Blockchain**: Hyperledger Fabric v2.5
- **Smart Contracts**: Go (Chaincode)
- **Backend API**: Node.js with Express.js
- **Database**: CouchDB (World State), PostgreSQL (Off-chain)
- **Frontend**: React.js
- **Authentication**: OAuth 2.0 + mTLS
- **Encryption**: AES-256, RSA-2048
- **Containerization**: Docker & Docker Compose

## Project Structure

```
helpcare-system/
├── network/
│   ├── docker-compose.yml
│   ├── crypto-config.yaml
│   ├── configtx.yaml
│   └── scripts/
│       ├── start-network.sh
│       ├── install-chaincode.sh
│       └── generate-artifacts.sh
├── chaincode/
│   ├── patient-records/
│   ├── appointments/
│   ├── prescriptions/
│   └── consent-management/
├── api/
│   ├── routes/
│   │   ├── patients.js
│   │   ├── providers.js
│   │   ├── appointments.js
│   │   └── records.js
│   ├── middleware/
│   ├── controllers/
│   └── server.js
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.js
│   └── package.json
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/
│   ├── setup-guide.md
│   ├── api-documentation.md
│   └── architecture.md
└── README.md
```

## Installation & Setup

### Prerequisites

- Docker & Docker Compose (v1.29+)
- Node.js (v14+)
- Go (v1.16+)
- Hyperledger Fabric binaries (v2.5)

### Quick Start

1. Clone the repository:

```bash
git clone https://github.com/Dhruv-A-Gandhi/helpcare-system.git
cd helpcare-system
```

2. Generate network artifacts:

```bash
cd network
bash scripts/generate-artifacts.sh
```

3. Start the Fabric network:

```bash
bash scripts/start-network.sh
```

4. Install chaincode:

```bash
bash scripts/install-chaincode.sh
```

5. Start the API server:

```bash
cd ../api
npm install
npm start
```

6. Start the frontend:

```bash
cd ../frontend
npm install
npm start
```

## Smart Contracts

### Patient Records Chaincode

- CreatePatientRecord()
- GetPatientRecord()
- UpdatePatientRecord()
- GetPatientHistory()

### Appointments Chaincode

- ScheduleAppointment()
- CancelAppointment()
- UpdateAppointmentStatus()
- QueryAppointments()

### Prescriptions Chaincode

- IssuePrescription()
- FulfillPrescription()
- GetPrescriptionHistory()
- ValidatePrescription()

### Consent Management Chaincode

- GrantConsent()
- RevokeConsent()
- QueryConsent()
- GetConsentAuditTrail()

## API Endpoints

### Patient Management

- `POST /api/patients` - Create new patient record
- `GET /api/patients/:id` - Retrieve patient information
- `PUT /api/patients/:id` - Update patient record
- `GET /api/patients/:id/records` - Get patient's medical records

### Provider Management

- `GET /api/providers` - List all providers
- `POST /api/providers/:id/verify` - Verify provider credentials

### Appointments

- `POST /api/appointments` - Schedule appointment
- `GET /api/appointments/:id` - Get appointment details
- `PUT /api/appointments/:id` - Update appointment

## Security & Privacy

- **mTLS**: All network communications encrypted
- **Attribute-Based Encryption**: Fine-grained access control
- **Privacy-Preserving Queries**: Selective disclosure of patient data
- **HIPAA Compliance**: Audit trails and access logs
- **Zero-Knowledge Proofs**: Verify claims without data exposure

## Testing

```bash
# Run unit tests
npm run test:unit

# Run integration tests
npm run test:integration

# Run end-to-end tests
npm run test:e2e
```

## Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit changes (`git commit -m 'Add YourFeature'`)
4. Push to branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

## Performance Metrics

- **Throughput**: ~100 transactions per second
- **Latency**: ~2-3 seconds average response time
- **Scalability**: Horizontal scaling via multi-org setup
- **Data Consistency**: Immediate consistency across network

## License

MIT License - see LICENSE file for details

## Contact & Support

- **Email**: dhruv.gandhi@ontariotech.ca
- **GitHub**: [@Dhruv-A-Gandhi](https://github.com/Dhruv-A-Gandhi)
- **Issues**: GitHub Issues tracker

## Acknowledgments

- Hyperledger Fabric Documentation
- HIPAA Privacy Rule Guidelines
- Healthcare Industry Standards (HL7, DICOM)
- Open-source community contributions
