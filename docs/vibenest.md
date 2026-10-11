# Deploy Scrumboy on VibeNest

[![Deploy to VibeNest](https://vibenest.net/deploy-to-vibenest.svg)](https://vibenest.net/deploy?repo=https://github.com/NikitaBabenko/scrumboy&branch=main)

This fork keeps Scrumboy's AGPL-3.0 license and adds a VibeNest entry point.
The initial upstream revision is `fb3321b29dc4ccd2f11129f97b63a8db5a6e6b1c`.

## Basic instance

1. Click the button and sign in to VibeNest.
2. Confirm repository `NikitaBabenko/scrumboy`, branch `main`, and the detected
   Dockerfile or Compose configuration. The application listens on port `8080`.
3. Keep a persistent volume at `/data` before storing important data. The
   Dockerfile's `VOLUME` declaration alone is not proof of durable platform storage.
   In Compose, verify that the configured volume survives resource recreation.
4. Use `SCRUMBOY_MODE=full` (the default). Open the assigned HTTPS URL and create
   your first owner. Keep the credentials private.
5. Create a durable board and a story. Sign out and sign back in to verify access.

The initial instance needs no SMTP, SSO, encryption key, or paid third-party service.
Optional email, password reset, 2FA, calendar, and push features have additional
requirements documented in the upstream environment and authentication guides.

VibeNest terminates HTTPS. Do not configure Scrumboy TLS certificate paths for this
basic setup. `SCRUMBOY_PUBLIC_BASE_URL` should be your assigned HTTPS origin when
using features that generate absolute links. `SCRUMBOY_TRUST_PROXY` affects
forwarded-header handling; use it only with the platform's trusted proxy setup.

## Free tier validation

The VibeNest Free tier provides 256 MB RAM, 0.5 vCPU, and 4 GB storage for a
three-month trial. A successful build does not establish suitability: measure
runtime memory, CPU and disk use, exercise authentication and collaboration, and
check SQLite data after restart and redeploy. Production suitability depends on
your workload. Acceptance results will be recorded after the live pilot.
