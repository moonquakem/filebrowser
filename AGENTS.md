# Repository Guidelines

## Project Structure & Module Organization
The backend is a Go application rooted at `main.go`. Core server and CLI code lives in `cmd/`, `http/`, `storage/`, `settings/`, `users/`, and `auth/`. Frontend code is in `frontend/`, with Vue views under `frontend/src/views`, reusable components under `frontend/src/components`, stores in `frontend/src/stores`, and API helpers in `frontend/src/api`. Embedded production assets are served from `frontend/dist`. Documentation source lives in `www/`, and Docker-based local deployment is defined in `compose.yaml`.

## Build, Test, and Development Commands
- `task build`: builds frontend assets and the backend binary.
- `go build -o filebrowser .`: builds the backend only.
- `go run .`: runs the server locally; if no database exists, quick setup creates one.
- `cd frontend && pnpm install && pnpm run dev`: starts the Vite frontend dev server.
- `cd frontend && pnpm run build`: type-checks and produces frontend assets in `frontend/dist`.
- `go test ./...`: runs all Go tests.
- `cd frontend && pnpm run test`: runs frontend tests with Vitest.
- `docker compose up -d`: starts the published container stack on `http://localhost:8000`.

## Coding Style & Naming Conventions
Follow standard Go formatting with `gofmt`; keep package names short and lowercase. Frontend code uses TypeScript, Vue SFCs, ESLint, and Prettier. Run `cd frontend && pnpm run lint` and `cd frontend && pnpm run format` before submitting UI changes. Use PascalCase for Vue components such as `HeaderBar.vue`, camelCase for TS utilities, and `_test.go` or `*.test.ts` for tests.

## Testing Guidelines
Place Go tests next to implementation files, for example `http/public_test.go` or `users/storage_test.go`. Frontend unit tests live under `frontend/src/**/__tests__` or as `*.test.ts` files, such as `frontend/src/utils/__tests__/upload.test.ts`. Add or update tests for bug fixes and behavior changes; at minimum, run the relevant package tests plus `go test ./...` when touching shared backend code.

## Commit & Pull Request Guidelines
Recent history uses short conventional prefixes such as `fix:`, `docs:`, `chore:`, and `chore(deps):`. Keep commit subjects imperative and focused. PRs should target `master`, explain the change, include extra implementation context for larger patches, and reference issues with closing keywords when applicable. If UI behavior changes, include screenshots or a short walkthrough. Do not submit direct translation edits; translations are managed through Transifex.
