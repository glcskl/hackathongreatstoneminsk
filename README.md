# hackathongreatstoneminsk — industrial safety inspection system

A Telegram Mini App for monitoring industrial safety compliance. The application works as a web interface inside Telegram, so an inspector opens it from a chat, walks through an equipment check and files the result without installing anything.

Built for the Space and Miran hackathon on 12 to 14 November 2025.


## Features

- Runs as a Telegram Mini App, launched from inside a chat
- Inspection checklists for registered equipment
- Step-by-step pass and fail capture with comments on each item
- Equipment records with their current inspection state
- Designed for a phone screen, as most inspections happen on the floor
- No build step and no framework, so it opens instantly over a mobile connection

## Tech stack

| Layer | Technology |
| --- | --- |
| Language | HTML, CSS, plain JavaScript |
| Platform | Telegram Mini App |
| Build tooling | none |
| Hosting | Static hosting |

## Getting started

### Requirements

- A static web server, or any hosting that serves files over HTTPS
- A Telegram bot token, to attach the web app

### Environment variables

None. Configuration is applied from inside the Telegram client, not through build-time environment variables.

### Installation

```bash
git clone https://github.com/glcskl/hackathongreatstoneminsk.git
cd hackathongreatstoneminsk
```

### Running

Serve the directory over HTTP, from the repository root or any local web server:

```bash
python -m http.server 8080
```

Then point a Telegram Web App button at the served URL. A Mini App must be served over HTTPS, so for anything beyond local testing use a tunnel or a hosting provider.

## Project structure

```
index.html      single-page application, the whole interface
equipment/      equipment records and check data
README.md       project notes from the hackathon
```

## Implementation notes

The interface is one HTML file. It loads the Telegram Web App script, reads the user from the init data the client passes, and renders checklists from the data in `equipment/`. There is no build tooling, no package manager and no framework, which keeps the payload small and the behaviour predictable.

## Notes

This is a hackathon project produced under a fixed deadline. It stores inspection results locally in the browser and has no server-side persistence, so it is not suitable for real compliance work.