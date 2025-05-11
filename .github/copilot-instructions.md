## Code Standards

### Required Before Each Commit

- Run `pnpm lint` to ensure code follows project standards
- Make sure all components follow Next.js App Router patterns
- Client components should be marked with 'use client' when they use browser APIs or React hooks
- When adding new functionality, make sure you update the README
- Make sure that the repository structure documentation is correct and accurate in the Copilot Instructions file
- Ensure all tests pass by running `pnpm test` in the terminal

### TypeScript and React Patterns

- Use TypeScript types for all props and data structures
- Follow React best practices (hooks, functional components)
- Use proper state management techniques
- Components should be modular and follow single-responsibility principle

### Credentials and Secrets

- Manage sensitive information (e.g., database credentials) using a `.env` file.
- Define all keys in the `.env` file using snake_case.
- Validate and ensure type safety of environment variables using `zod` before referencing them in code.

```ts
import "dotenv/config";
import { z } from "zod";

const EnvSchema = z.object({
  DB_FILE_NAME: z.string(),
});

export const env = EnvSchema.parse(process.env);
```

## Development Flow

- Install dependencies: `pnpm install`
- Development server: `pnpm dev`
- Build: `pnpm build`
- Test: `pnpm test`
- Lint: `pnpm lint`

## Repository Structure

- `docs/`: Documentation files
- `src/`: Structure the `src` directory in accordance with [Feature-Sliced Design](https://feature-sliced.github.io/documentation/).
- `src/app/`: Everything that makes the app run — routing, entrypoints, global styles, providers. But, if use Next.js App Router,  pages and layouts organized by route.
- `src/pages/`: Full pages or large parts of a page in nested routing.
- `src/widgets/`: Large self-contained chunks of functionality or UI, usually delivering an entire use case.
- `src/features/`: Reused implementations of entire product features, i.e. actions that bring business value to the user.
- `src/entities/`: Business entities that the project works with, like `user` or `product`.
- `src/shared/`: Reusable functionality, especially when it's detached from the specifics of the project/business, though not necessarily.
  - `src/shared/ui/`: Everything related to UI display: UI components, date formatters, styles, etc.
  - `src/shared/api/`: Backend interactions: request functions, data types, mappers, etc.
  - `src/shared/model/`: The data model: schemas, interfaces, stores, and business logic.
  - `src/shared/lib/`: Library code that other modules on this slice need.
  - `src/shared/config/`: Configuration files and feature flags.
- `public/`: Static assets
- `scripts/`: Scripts for various tasks, such as deployment or setup
- `test/`: Test files and test utilities
- `README.md`: Project documentation

## Key Guidelines

1. Make sure to evaluate the components you're creating, and whether they need 'use client'
2. Images should contain meaningful alt text unless they are purely for decoration. If they are for decoration only, a null (empty) alt text should be provided (alt="") so that the images are ignored by the screen reader.
3. Follow Next.js best practices for data fetching, routing, and rendering
4. Use proper error handling and loading states
5. Optimize components and pages for performance
