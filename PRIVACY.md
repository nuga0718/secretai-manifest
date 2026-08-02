# BIMILAI — Privacy Policy

_Last updated: 2026-07-27_

BIMILAI is a native Android app that runs an AI assistant **entirely on your
device**. This policy describes exactly what the app does and does not do with
your data. It is written to be accurate to the app as built, not aspirational.

## Summary

- All AI inference runs **on-device**. Your prompts and the model's responses
  never leave your phone.
- Conversations are stored **only locally**, in a database encrypted with
  **AES-256 via SQLCipher**.
- The app sends **no conversation data, analytics, or telemetry** to any server.
- The only network activity is a one-time **model download** from Hugging Face
  and a small **model-list (manifest) fetch**.

## Data we collect: none off-device

BIMILAI does not have a backend server and does not have an account system.
We — the developer — receive **no data from your use of the app**. Specifically:

- No conversation content, prompts, or responses are transmitted anywhere.
- No usage analytics, crash telemetry, advertising identifiers, or device
  fingerprints are collected or transmitted.
- No personal information (name, email, contacts, location) is requested,
  collected, or transmitted.

## Where your data lives

- **Conversations** (messages, titles, timestamps, and any images you attach)
  are written to a local database on the device.
- That database is encrypted at rest with **AES-256 using SQLCipher**. The
  encryption key is held in the **Android Keystore** and never leaves the
  device.
- Because storage is local and encrypted, your chat history is accessible only
  on your device, through the app, behind the app lock.

## On-device AI inference

The assistant is powered by **Google's Gemma** models (Gemma 4, E2B / E4B),
executed on-device through the **LiteRT-LM** runtime. Prompts and images you
send to the assistant are processed locally by the model. They are **not** sent
to Google, to us, or to any third party for inference.

## Network use (the only times the app goes online)

1. **Model download (one-time per model).** Model files are downloaded directly
   from **Hugging Face**
   (`https://huggingface.co/<repo>/resolve/main/<file>`; the repositories are
   the ungated `litert-community` / Gemma model mirrors referenced by the app's
   manifest). The download is verified against a SHA-256 checksum before use.
2. **Model manifest fetch.** The app fetches a small static JSON file listing
   the available models and their checksums from
   `https://raw.githubusercontent.com/nuga0718/secretai-manifest/main/manifest.json`.

Neither request includes your conversations or any personal identifiers. These
requests are standard file downloads served by Hugging Face and GitHub; their
own logs (e.g. your IP address making the request) are governed by those
providers' privacy policies. No authentication token or account is required.

## Security controls

- **Biometric app lock.** Access to the app can be gated behind device
  biometrics (fingerprint / face), with a configurable auto-lock interval.
- **Encrypted database.** AES-256 (SQLCipher); key stored in the Android
  Keystore so it survives biometric re-enrollment.
- **Screen capture protection.** The app sets `FLAG_SECURE`, preventing
  screenshots and screen recording of its content.
- **No cloud backup.** `allowBackup` is disabled, so chat data is not copied to
  cloud backup services.

## Your control over your data

- **Delete a conversation:** removes that conversation from the local encrypted
  database.
- **Delete all conversations:** clears your entire chat history from the device.
- **Delete a model:** removes a downloaded model file from the device.
- **Uninstall:** removing the app deletes its local data, including the
  encrypted database and any downloaded models.

BIMILAI uses the package ID `com.hanbae.bimilai`, which Android treats as a
fresh application UID and storage boundary. Data from earlier package IDs such
as `kr.hanbae.bimilai` or `kr.spherecorp.secretai` is neither migrated nor
removed by installing BIMILAI.

## Children's privacy

The app collects no personal data from anyone, including children.

## Changes to this policy

If the app's data practices change, this document will be updated, and the
"Last updated" date above will reflect the change.

## Contact

For privacy questions, contact the developer at the email associated with the
app's distribution listing.
