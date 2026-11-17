# Echora Messenger

A lightweight, invite-limited web messaging prototype built with Supabase. It includes a custom username/PIN entry flow, shared messages, and media uploads.

## Features

- Username and PIN entry screens.
- Load and send chat messages.
- Copy and delete message actions.
- Media upload and preview.
- Profile data integration.
- Responsive browser interface.

## Technology

- HTML, CSS, and vanilla JavaScript.
- Supabase JavaScript client.
- Supabase database and storage.
- Font Awesome icons via CDN.

## Backend and authentication notes

The current frontend connects to Supabase resources including `profiles`, `messages`, and `media`.

The existing username/PIN flow is a legacy custom implementation, **not Supabase Auth**. PIN values are compared in the browser and the selected profile is cached in local storage. This is not suitable for private accounts or sensitive conversations.

Before using this with real users:

1. Migrate registration and login to Supabase Auth.
2. Remove PIN values from the `profiles` table. Never store passwords or PINs in plaintext.
3. Enforce Row Level Security for profiles and messages, including sender-identity checks.
4. Restrict storage access to authenticated users.
5. Validate uploaded file types and sizes.
6. Confirm users cannot read, edit, or delete another user's private data.

A Supabase publishable/anon key is intended for browser use, but it does not replace access control. Never put a service-role key in frontend code.

## Run locally

Serve the repository root:

```bash
python -m http.server 8000
```

Open http://localhost:8000 after configuring the Supabase project.

## Deployment

This is a static frontend that can be hosted with GitHub Pages. Supabase remains a separate backend dependency.

## Security status

Do not use the current custom PIN flow for real private accounts until authentication and database policies are migrated and reviewed.

## License

No license is currently specified. All rights remain with the repository owner unless a license is added.
