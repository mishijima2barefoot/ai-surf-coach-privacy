# AI Surf Coach — Privacy

AI Surf Coach provides real-time coaching and feedback for surfers using on-device and server-assisted computer vision and ML models while prioritizing user privacy.

## Why this project

Surf coaching benefits from visual feedback, but video and biometric data are sensitive. This repository demonstrates an approach that delivers actionable coaching while minimizing retention and exposure of personal data.

## Key features

- Real-time form and wave-detection feedback
- On-device preprocessing to reduce sensitive data sent to servers
- Differentially minimized telemetry for model improvements (opt-in)
- Clear data handling and opt-out controls

## Quickstart

1. Clone the repo:

   git clone https://github.com/mishijima2barefoot/ai-surf-coach-privacy.git

2. Install dependencies (example, adjust for your stack):

   - Python/Node example:
     - python -m venv .venv
     - source .venv/bin/activate
     - pip install -r requirements.txt

   or

     - npm install

3. Configure environment variables (see `.env.example`):

   - COACH_API_KEY: API key for analytics (optional)
   - PRIVACY_MODE: `strict` or `balanced`

4. Run locally:

   - python app.py
   - or npm start

## Privacy & Data Handling

This project follows privacy-by-design principles. Important behaviors:

- Local-first processing: wherever possible, video frames and pose estimation run on the user's device. Only anonymized or derived features (e.g., keypoint coordinates, aggregated metrics) are sent to servers when strictly necessary.

- No raw video retention: raw video is never stored on servers by default. If a user explicitly chooses to upload a clip for review, that clip is stored encrypted and retained only for a configurable short period.

- Minimal telemetry and opt-in learning: model improvement telemetry is opt-in. When enabled, telemetry contains minimal metadata and aggregated metrics; personally identifying information (PII) is excluded.

- Pseudonymization & consent: any identifiers are replaced with pseudonymous tokens. Clear consent flows are required before any data leaves the device.

- Right to delete & audit logs: users can request deletion of their data; deletion workflows and audit logs are documented and verifiable.

- Third-party services: third-party services are documented in `third_parties.md` and undergo privacy review before integration.

## Architecture

High-level components:

- Client (mobile/web): captures video, runs on-device models, displays feedback
- Edge processing: optional server-side transient processing for heavier models
- Backend: stores pseudonymized records, manages opt-in telemetry and model training pipelines

Data flow principles:
- Keep raw data on-device
- Transmit only derived features when needed
- Use short-lived storage and encryption in transit and at rest

## Development

- Follow the repo's CONTRIBUTING.md for coding standards and PR workflow.
- Run tests with `pytest` or `npm test` depending on the language stack used in this repo.

## Contributing

Contributions are welcome. Please open issues for discussion before large changes. Include privacy impact assessments for features that affect data collection or retention.

## License

This project is licensed under the MIT License — see the LICENSE file for details.

## Contact

Maintainer: mishijima2barefoot

Security & privacy concerns: Please open an issue or email the maintainer listed in the repo.