# Finance App
Aplikasi manajemen keuangan untuk siswa SMK dengan platform Web dan Mobile.

---

## 🛠️ Tech Stack

### Backend
- **Runtime**: Deno / Node.js (pilih salah satu)
- **Framework**: Hono
- **Language**: TypeScript
- **Database**: Turso (LibSQL)
- **ORM**: Drizzle ORM
- **Auth**: Better-auth
- **Hosting**: Deno Deploy / Vercel Edge

### Web Platform
- **Framework**: Nuxt 3
- **Language**: TypeScript
- **Hosting**: Vercel
- **State Management**: Pinia (built-in Nuxt)
- **API Client**: useFetch / $fetch (Nuxt composables)

### Mobile Platform
- **Framework**: Expo (React Native)
- **Language**: TypeScript
- **API Client**: Axios / Fetch API
- **Navigation**: Expo Router
- **State Management**: Zustand / TanStack Query

---

## 🎯 App Ideas & Features

### Option 1: Uang Jajan Harian
- [ ] Catat pemasukan (uang saku, uang jajan)
- [ ] Catat pengeluaran harian (kantin, fotokopi, transport)
- [ ] Kategori pengeluaran custom
- [ ] Grafik pengeluaran per kategori
- [ ] Reminder limit pengeluaran
- [ ] Export laporan (PDF/CSV)

### Option 2: Tabungan & Target
- [ ] Set target tabungan
- [ ] Progress bar target
- [ ] Kalkulator estimasi waktu
- [ ] Multiple targets
- [ ] Riwayat tabungan
- [ ] Notifikasi milestone

### Option 3: Patungan/Split Bill
- [ ] Buat grup patungan
- [ ] Split bill otomatis
- [ ] Track siapa sudah bayar
- [ ] Reminder pembayaran
- [ ] Riwayat patungan per grup
- [ ] Export summary

### Option 4: Kas Kelas
- [ ] Kelola iuran kelas
- [ ] Dashboard pemasukan/pengeluaran
- [ ] Laporan bulanan otomatis
- [ ] Notifikasi iuran
- [ ] Role: Admin & Member
- [ ] Approval system untuk pengeluaran

---

## 📊 Database Schema (Draft)

### Users Table

```sql
- id (primary key)
- email (unique)
- name
- avatar_url
- created_at
- updated_at
```

### Transactions Table

```sql
- id (primary key)
- user_id (foreign key)
- type (income/expense)
- amount
- category_id (foreign key)
- description
- date
- created_at
- updated_at
```

### Categories Table

```sql
- id (primary key)
- user_id (foreign key, nullable for default)
- name
- icon
- color
- type (income/expense)
- is_default (boolean)
```

### Targets Table (untuk fitur tabungan)

```sql
- id (primary key)
- user_id (foreign key)
- name
- target_amount
- current_amount
- deadline
- status (active/completed/cancelled)
- created_at
- updated_at
```

---

## 🔌 API Endpoints (Draft)

### Authentication
- `POST /api/auth/register` - Register user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user

### Transactions
- `GET /api/transactions` - Get all transactions (with filters)
- `GET /api/transactions/:id` - Get single transaction
- `POST /api/transactions` - Create transaction
- `PUT /api/transactions/:id` - Update transaction
- `DELETE /api/transactions/:id` - Delete transaction
- `GET /api/transactions/summary` - Get summary (total income/expense)

### Categories
- `GET /api/categories` - Get all categories
- `POST /api/categories` - Create custom category
- `PUT /api/categories/:id` - Update category
- `DELETE /api/categories/:id` - Delete category

### Targets (if needed)
- `GET /api/targets` - Get all targets
- `POST /api/targets` - Create target
- `PUT /api/targets/:id` - Update target
- `DELETE /api/targets/:id` - Delete target

---

## 📁 Project Structure

### Backend (Hono)
```
backend/
├── src/
│   ├── routes/
│   │   ├── auth.ts
│   │   ├── transactions.ts
│   │   ├── categories.ts
│   │   └── targets.ts
│   ├── db/
│   │   ├── schema.ts
│   │   └── client.ts
│   ├── middleware/
│   │   └── auth.ts
│   ├── utils/
│   │   └── validation.ts
│   └── index.ts
├── drizzle.config.ts
└── package.json
```

### Web (Nuxt)
```
web/
├── pages/
│   ├── index.vue
│   ├── login.vue
│   ├── register.vue
│   ├── dashboard.vue
│   └── transactions/
│       ├── index.vue
│       └── [id].vue
├── components/
│   ├── TransactionForm.vue
│   ├── TransactionList.vue
│   └── CategoryPicker.vue
├── composables/
│   ├── useAuth.ts
│   └── useTransactions.ts
├── stores/
│   └── auth.ts
└── nuxt.config.ts
```

### Mobile (Expo)
```
mobile/
├── app/
│   ├── (auth)/
│   │   ├── login.tsx
│   │   └── register.tsx
│   ├── (tabs)/
│   │   ├── index.tsx
│   │   ├── transactions.tsx
│   │   └── profile.tsx
│   └── _layout.tsx
├── components/
│   ├── TransactionCard.tsx
│   └── CategoryIcon.tsx
├── services/
│   └── api.ts
├── stores/
│   └── authStore.ts
└── package.json
```

---

## ✅ Development Roadmap

### Phase 1: Setup & Foundation
- [ ] Setup backend (Hono + Drizzle + Turso)
- [ ] Setup better-auth
- [ ] Create database schema
- [ ] Setup Nuxt web project
- [ ] Setup Expo mobile project
- [ ] Configure API connections

### Phase 2: Core Features (MVP)
- [ ] Authentication (login/register)
- [ ] Create transaction
- [ ] View transactions list
- [ ] Edit/Delete transaction
- [ ] Categories management
- [ ] Dashboard summary

### Phase 3: Additional Features
- [ ] Grafik/Charts
- [ ] Export laporan
- [ ] Notifikasi
- [ ] Target/Goals (optional)
- [ ] Dark mode
- [ ] Multi-language (optional)

### Phase 4: Polish & Deploy
- [ ] Testing
- [ ] Bug fixes
- [ ] Performance optimization
- [ ] Deploy backend
- [ ] Deploy web (Vercel)
- [ ] Publish mobile (Expo)

---

## 🔗 Important Links

### Documentation
- [Hono Docs](https://hono.dev/)
- [Drizzle ORM](https://orm.drizzle.team/)
- [Turso Docs](https://docs.turso.tech/)
- [Better Auth](https://www.better-auth.com/)
- [Nuxt 3 Docs](https://nuxt.com/)
- [Expo Docs](https://docs.expo.dev/)

### Resources
- [Turso + Drizzle Guide](https://docs.turso.tech/sdk/ts/orm/drizzle)
- [Hono + Deno Deploy](https://hono.dev/getting-started/deno)
- [Nuxt Best Practices](https://nuxt.com/docs/guide/going-further)

---

## 📝 Notes & Decisions

### Backend Hosting Decision
- **Option A**: Deno Deploy (recommended)
  - Pros: Fast, native TS, edge runtime
  - Cons: Check better-auth compatibility
  
- **Option B**: Vercel Edge
  - Pros: Better-auth guaranteed support
  - Cons: Slightly slower than Deno

**Decision**: _(to be decided)_

### App Type Decision
- **Chosen App**: _(pilih salah satu dari 4 opsi)_
- **Reasoning**: _(alasan pemilihan)_

### Additional Notes
- _(catatan-catatan penting selama development)_

---

## 🐛 Known Issues
- _(track bugs dan issues di sini)_

---

## 💡 Future Ideas
- _(fitur-fitur yang bisa ditambah di masa depan)_
