# Procura — Procurement & Contracts

Phase 1 React, Vite, TypeScript, Tailwind CSS, and Lucide Icons workspace for an existing Supabase project. This app does not create, migrate, or modify database objects.

## Run locally

1. Copy `.env.example` to `.env`.
2. Set `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` to your Supabase project values.
3. Run `npm install`, then `npm run dev`.

The Supabase anon key is intended for browser use. Protect data with the appropriate Supabase Row Level Security policies; never put a service-role key in this app.

## Existing database objects

- Login uses Supabase Auth email/password.
- The dashboard reads `vw_contracts_summary` and `vw_po_summary`.
- Companies & Contacts uses the `companies` and `contacts` tables. Its forms expect `companies` columns `id`, `name`, `legal_name`, `registration_number`, `tax_number`, `email`, `phone`, `country`, and `address`; and `contacts` columns `id`, `company_id`, `first_name`, `last_name`, `email`, `phone`, and `job_title`.
- Contact `company_id` values are matched to `companies.id`.

The app surfaces Supabase query errors in the UI. If your existing tables use different column names, update the field mapping and forms in `src/pages/CompaniesPage.tsx` to match; no database changes are required.

## Locale

Use the sidebar language control to switch between English (LTR) and Arabic (RTL). The selection is stored in browser local storage.
