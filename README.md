# Yuvraj Singh Negi — Portfolio

A personal portfolio and freelance inquiry site built with Next.js App Router, React, TypeScript, Tailwind CSS, Framer Motion, Lucide and optional Resend email delivery.

## Run locally

- Install Node.js 20.9 or newer.
- Run `npm install`.
- Copy `.env.example` to `.env.local` and fill in the Resend credentials and recipient if you want email delivery. Leave it unconfigured to use the WhatsApp fallback.
- Run `npm run dev` and open [http://localhost:3000](http://localhost:3000).

## Edit your portfolio

- Update personal, education, phone, social and contact values in `src/data/profile.ts` (`profile`). LinkedIn and email are intentionally hidden until non-empty valid values are set.
- Update skills in `src/data/profile.ts` (`skills`). No proficiency claims are displayed.
- Replace or add project entries in `src/data/profile.ts` (`projects`). Entries are currently clearly labeled sample concepts, with no client or completed-work claims. Add real project artwork to `public/images` and adjust the `visual` presentation in `src/app/page.tsx` if desired. Set real repository and live URLs once available.
- Edit offered services in `src/data/profile.ts` (`services`).
- Replace `public/images/yuvraj.jpeg` to change the hero portrait.

## Contact form & email

The contact endpoint validates all values on the server, includes a hidden honeypot field and limits each IP to five submissions per ten minutes. Without both `RESEND_API_KEY` and `CONTACT_TO_EMAIL`, it returns a WhatsApp link with the submitted project information prefilled. Email submissions use the visitor's email as reply-to. Configure a verified sender in `RESEND_FROM_EMAIL` for production. The in-memory rate limit is suitable for a single process; use a shared store (for example, managed Redis) if deploying multiple serverless instances and needing globally enforced limits.

## Production build

Run `npm run build`, then `npm start` to serve the production build locally.

## Deploy to Vercel

1. Push this project to a Git repository and import it in Vercel.
2. Add the optional Resend values in Vercel Project Settings → Environment Variables.
3. Deploy. Vercel detects Next.js automatically.
4. Replace the placeholder canonical domain `example.com` in `src/app/robots.ts` and `src/app/sitemap.ts`, and set `metadataBase` in `src/app/layout.tsx` when the domain is known.
5. In Vercel Project Settings → Domains, add your domain and follow the displayed DNS instructions at your registrar. Wait for DNS verification and HTTPS provisioning.
