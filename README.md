
@'
# Docker & Container Security — FestPass

## Student Details
- **Name:** Arya Singh Vats
- **Registration Number:** 202401100100062
- **Assigned Port:** 142

## Project Overview
FestPass is a three-tier registration application containerized using Docker. It uses a Flask backend, an Nginx frontend, and a PostgreSQL database.

## Architecture
- **Frontend:** Nginx serving the web interface
- **Backend:** Python Flask REST API
- **Database:** PostgreSQL
- **Orchestration:** Docker Compose
- **Security Scanning:** Trivy
- **Image Signing:** Cosign

## Run the Application

Create your local `.env` file using `.env.example` and configure the required values.

Start the application:

```bash
docker compose up -d --build
```

Open: http://localhost:142

Check running containers:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs
```

Stop the application:

```bash
docker compose down
```

To stop without deleting persistent database data, do not add `-v`.

## Security Scanning

The backend image was scanned using Trivy. Reports are available in `reports/`.

- Initial scan: `reports/trivy-before.txt`
- Hardened image scan: `reports/trivy-after.txt`

The hardened image was checked for critical vulnerabilities using:

```bash
trivy image --severity CRITICAL --ignore-unfixed --exit-code 1 fest-backend:0.2
```

## Docker Hub

Docker Hub namespace: `aryasinghvats`

Image: `aryasinghvats/fest-backend:1.0.0`

Publication status and digest should be confirmed after a successful push.

## Evidence

Place assessment screenshots in the `screenshots/` directory, using the filenames specified in the assignment.

## Security Notes
- Do not commit `.env`, credentials, or private signing keys.
- `.env.example` contains configuration placeholders.
- Keep the Cosign private key (`cosign.key`) secret. Only the public key may be committed.
'@ | Set-Content -Encoding UTF8 README.md

git add README.md
git commit -m "Add project README and run instructions"
