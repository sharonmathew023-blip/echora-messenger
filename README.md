# Echora Messenger

A small, invite-limited web chat project built around Supabase. The interface includes account access, conversations, and media-related chat features.

## Features

- Login and account creation UI.
- Chat message loading and sending.
- Message copy and delete actions.
- Media upload and preview flows.
- Profile data integration.
- Responsive browser interface.

## Technology

- HTML, CSS, and vanilla JavaScript.
- Supabase JavaScript client.
- Supabase Auth and database/storage services.
- Font Awesome icons via CDN.

## Backend setup

The frontend currently connects to a Supabase project. To run your own instance:

1. Create a Supabase project.
2. Configure the project URL and publishable/anon key in the client initialization in `index.html`.
3. Create and configure the required `profiles`, `messages`, and `media` tables/buckets to match the queries in the application.
4. Configure Supabase Auth redirect URLs for your local and deployed origins.
5. Enable and test Row Level Security policies for every table and storage bucket before allowing real users.

A Supabase publishable/anon key is intended for browser use, but it is not a substitute for access control. Never put a service-role key in frontend code. Review database and storage policies before using real personal messages or files.

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
