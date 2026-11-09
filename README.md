# Echora Messenger

A small, invite-limited web chat prototype built around Supabase. The interface includes a custom username/PIN screen, shared messages, and media uploads.

## Features

- Custom username and PIN entry screens.
- Chat message loading and sending.
- Message copy and delete actions.
- Media upload and preview flows.
- Profile data integration.
- Responsive browser interface.

## Technology

- HTML, CSS, and vanilla JavaScript.
- Supabase JavaScript client.
- Supabase database and storage.
- Font Awesome icons via CDN.

## Backend setup

The current frontend connects directly to a Supabase project and queries the `profiles`, `messages`, and `media` resources.

The current login is a legacy custom username/PIN flow stored in the `profiles` table. **It is not Supabase Auth.** The current implementation compares PIN values in the browser and caches the selected profile in local storage. Do not use this design for private accounts or sensitive conversations.

Before using real users:

1. Migrate account creation and login to Supabase Auth.
2. Remove PIN values from the `profiles` table and never store passwords or PINs in plaintext.
3. Enforce Row Level Security for profiles and messages, including sender identity checks.
4. Restrict storage access to authenticated users and validate uploaded file types and sizes.
5. Review policies so one user cannot read, alter, or delete another user's private data.

A Supabase publishable/anon key is intended for browser use, but it is not a substitute for access control. Never put a service-role key in frontend code.

## Run locally

Serve the repository root:

```bash
python -m http.server 8000
```

Open http://localhost:8000 after configuring the Supabase project.

## Deployment

This is a static frontend and can be hosted with GitHub Pages. Supabase remains a separate backend dependency.

## License

No license is currently specified. All rights remain with the repository owner unless a license is added.
