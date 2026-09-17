# NoteHub

GoIT React homework (`05-notehub`): a single-page note manager that talks to the public [NoteHub API](https://notehub-public.goit.study/api). You can search, paginate, create, and delete notes from the browser.

## Live demo

[https://05-notehub-five-lime.vercel.app](https://05-notehub-five-lime.vercel.app)

## Features

- **Note list** — loads notes from the API (12 per page) and shows title, content, and tag (`Todo`, `Work`, `Personal`, `Meeting`, `Shopping`).
- **Search** — text search is sent to the API after a 300 ms debounce; the page resets to 1 on a new query.
- **Pagination** — page controls appear when there is more than one page; previous results stay visible while the next page loads (`keepPreviousData`).
- **Create note** — “Create note +” opens a modal form (title, content, tag) with Formik and Yup validation:
  - title: required, 3–50 characters
  - content: optional, up to 500 characters
  - tag: required, one of the tags listed above
- **Delete note** — each list item has a Delete button that removes the note via the API and refreshes the list.
- **Modal** — rendered with a React portal; closes on Escape, backdrop click, or Cancel; body scroll is locked while it is open.
- **Status messages** — “Loading notes…” while the first request is in flight, and “Something went wrong.” on a failed fetch.

## Tech stack

- [React](https://react.dev/) 19 + [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vite.dev/)
- [TanStack Query](https://tanstack.com/query) for server state
- [Axios](https://axios-http.com/) for HTTP (`Authorization: Bearer` token)
- [Formik](https://formik.org/) + [Yup](https://github.com/jquense/yup) for the create form
- [react-paginate](https://github.com/AdeleD/react-paginate)
- [use-debounce](https://github.com/xnimorz/use-debounce)
- CSS Modules and [modern-normalize](https://github.com/sindresorhus/modern-normalize)

## Getting started

Requirements: Node.js and npm.

```bash
git clone https://github.com/groteskzp/05-notehub.git
cd 05-notehub
npm install
```

Create a `.env` file in the project root with your NoteHub token (the app reads `import.meta.env.VITE_NOTEHUB_TOKEN`):

```bash
VITE_NOTEHUB_TOKEN=your_token_here
```

Start the development server:

```bash
npm run dev
```

Open the local URL printed by Vite (usually `http://localhost:5173`).

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Type-check with `tsc -b` and build for production |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |
