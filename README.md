# Mother Care Givers Platform

A comprehensive donation platform built with React, Node.js, Express, and MongoDB to support mothers in need.

## Features

- User Authentication (Donors & Administrators)
- Secure M-Pesa Payment Integration
- Donation Management
- Admin Dashboard
- Real-time Transaction Tracking
- Responsive Design

## Tech Stack

- Frontend: React, TailwindCSS
- Backend: Node.js, Express
- Database: MongoDB
- Authentication: JWT
- Payment: M-Pesa Integration

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB
- M-Pesa Developer Account

### Environment Variables

Create a `.env` file in the root directory:

```env
MONGODB_URI=mongodb://localhost:27017/mother-care-givers
JWT_SECRET=your_jwt_secret_key
PORT=5000

# M-Pesa Credentials
MPESA_CONSUMER_KEY=your_consumer_key
MPESA_CONSUMER_SECRET=your_consumer_secret
MPESA_PASSKEY=your_passkey
MPESA_SHORTCODE=your_shortcode
MPESA_CALLBACK_URL=your_callback_url
```

### Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm run dev
   ```

## API Documentation

### Authentication Endpoints

#### POST /api/auth/register
Register a new user
```json
{
  "name": "string",
  "email": "string",
  "phone": "string",
  "password": "string",
  "role": "user | admin"
}
```

#### POST /api/auth/login
Login user
```json
{
  "email": "string",
  "password": "string"
}
```

### Donation Endpoints

#### POST /api/donations
Create a new donation
```json
{
  "amount": "number",
  "phone": "string"
}
```

#### GET /api/donations/my-donations
Get user's donation history

### Admin Endpoints

#### GET /api/admin/donations
Get all donations (admin only)

#### PATCH /api/admin/donations/:id
Update donation status
```json
{
  "status": "pending | completed | failed"
}
```

#### GET /api/admin/stats
Get admin dashboard statistics

## Database Schema

### User Model
```typescript
{
  name: string;
  email: string;
  phone: string;
  password: string;
  role: "user" | "admin";
  createdAt: Date;
  updatedAt: Date;
}
```

### Donation Model
```typescript
{
  user: ObjectId;
  amount: number;
  transactionId: string;
  status: "pending" | "completed" | "failed";
  paymentMethod: "mpesa";
  createdAt: Date;
  updatedAt: Date;
}
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.