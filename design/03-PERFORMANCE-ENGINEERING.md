## 4. UX performance and perceived speed

Perceived performance is part of product quality. Do not optimize only for fast office Wi-Fi. Consider slow networks, cold starts, older devices, and repeat visits.

### MUST

1. Inspect the current loading sequence and identify serial dependencies, redundant requests, blocking work, and repeated loading states before changing code.
2. Do not block the whole screen on data that is not necessary for the first useful view. Render the stable shell and critical content as soon as possible.
3. Avoid waterfalls: independent requests should run concurrently where dependencies and rate limits allow.
4. Keep expensive work off the critical rendering path. Defer non-critical modules, images, and secondary data when appropriate.
5. Preserve correctness, security, and authorization. Never treat cached client data as authoritative for permissions, access control, billing, or sensitive decisions.
6. Measure before and after where possible. Report actual measured values, test conditions, and any trade-offs. Never claim a speedup without evidence.

### SHOULD

- Use stale-while-revalidate or cached snapshots for non-sensitive, low-risk display data where appropriate. Show cached content immediately, refresh in the background, and reconcile updates safely.
- Persist only what is useful and safe. Choose storage based on size, sensitivity, lifecycle, and consistency needs; a small preference/cache may fit local storage, while larger or relational data may need IndexedDB or a backend cache.
- Use request deduplication, cancellation, timeouts, retries with backoff, and appropriate cache headers where they fit the existing architecture.
- Avoid duplicate loading screens. Keep layout dimensions stable to reduce layout shift.
- Lazy-load below-the-fold media and non-critical features. Give important hero imagery explicit dimensions and suitable loading priority.
- Optimize images with modern formats and responsive sizes. Avoid loading oversized assets.
- Monitor Core Web Vitals and real user performance when analytics are available.

### Loading patterns

- **Skeleton loaders:** Use only when loading is long enough to justify a placeholder (a delay of roughly 300ms is a useful starting point). Match the eventual content geometry so layout does not jump. Prefer reusing the same layout structure/component between loading and loaded states.
- **Optimistic updates:** Use for low-risk, reversible actions such as likes, simple toggles, and renames. Update immediately, then reconcile with the server. On failure, roll back and show a clear recovery message. Do not optimistically grant permissions, mark payments complete, or perform irreversible actions.
- **Progress indicators:** Show determinate progress only when the amount of work is known. Use indeterminate indicators for unknown-duration work. Do not show fake percentages.
- **Cached first paint:** May show a recent snapshot while refreshing, but clearly handle stale or invalid data and never allow stale data to authorize protected actions.
- **Parallel requests:** Parallelize independent calls; preserve order only for genuine dependencies. Avoid unbounded request fan-out.

### Backend boundary

If an improvement requires backend changes, API contract changes, server cache configuration, authentication policy, or infrastructure access unavailable in the current environment, do not fake it in the frontend. Document it as a backend/deployment dependency and implement only the safe client-side portion.

---

## 5. Engineering and implementation standards

### MUST

1. Inspect the repository before editing: framework, package manager, app structure, existing components, design tokens, routing, state management, data fetching, tests, linting, and build scripts.
2. Reuse existing components, dependencies, patterns, and code style wherever they are sound. Do not add a library for something the project already handles well.
3. Avoid introducing a new design system or state-management library for a small visual improvement.
4. Keep changes scoped, accessible, responsive, and maintainable. Do not break existing product behavior to achieve a visual result.
5. Do not rewrite unrelated code or perform broad refactors without necessity.
6. Use semantic HTML and accessible names. Prefer native elements when they provide the right behavior.
7. Keep content and layout resilient to long strings, localization, empty data, errors, and loading states.
8. Test each meaningful change. Run the relevant lint, typecheck, unit/integration tests, and build commands available in the project.
9. Do not claim tests passed unless they were actually run and passed. Report unavailable checks and environment blockers.
10. Never hardcode secrets, credentials, private endpoints, or user-specific sensitive data into the client.

### SHOULD

- Use existing CSS variables/theme tokens rather than scattered one-off values.
- Keep components cohesive and avoid excessive abstraction for one-off UI.
- Use stable keys and predictable state transitions.
- Avoid unnecessary rerenders and expensive work in render paths.
- Use semantic buttons and links; do not use clickable `div` elements when a native control fits.
- Ensure loading, empty, error, disabled, and success states are part of the implementation, not an afterthought.
- Keep motion and visual effects performant on modest hardware and mobile devices.

---

## 11. Performance and perceived speed

Performance is part of product quality. A beautiful screen that waits on unnecessary requests, shifts while loading, or freezes during input is not finished.

### 11.1 Loading architecture

- **MUST:** Identify the minimum data required to render a useful first screen. Do not block the entire application on unrelated requests.
- **SHOULD:** Start independent requests in parallel. Avoid sequential waterfalls unless one request truly depends on another.
- **SHOULD:** Render the application shell and useful cached data while revalidating in the background when security and freshness rules permit.
- **SHOULD:** Separate critical-path data from below-the-fold or secondary data. Load secondary panels when needed or when idle.
- **SHOULD:** Use route-level/code splitting for large features and defer non-critical scripts.
- **MUST:** Reserve dimensions for images, embeds, ads, charts, and async content to avoid layout shifts.
- **SHOULD:** Use responsive images, modern formats where supported, and appropriate `srcset`/`sizes`. Lazy-load offscreen media; do not lazy-load the main above-the-fold/LCP image.
- **SHOULD:** Cache according to data volatility and sensitivity. Define invalidation, expiry, and logout behavior; never cache private data in a way that leaks across accounts.
- **MUST:** Treat local cached data as provisional, not authoritative for authorization, payment, subscription entitlements, or other sensitive decisions. Revalidate those with the server before granting access.
- **SHOULD:** Abort obsolete requests, debounce high-frequency search, and avoid state updates from stale responses.

### 11.2 Performance budgets and measurement

- **MUST:** Measure before and after optimization. Do not claim “10x faster” based only on a local impression.
- **SHOULD:** Track Core Web Vitals at the 75th percentile, segmented by mobile and desktop: LCP ≤ 2.5s, INP ≤ 200ms, CLS ≤ 0.1 as good targets.
- **SHOULD:** Use Lighthouse for lab diagnostics and real-user monitoring / field data for production behavior. Lab scores are not a substitute for field experience.
- **SHOULD:** Inspect bundle size, route chunks, long tasks, image weight, font loading, network waterfalls, and third-party scripts.
- **SHOULD:** Test throttled network and CPU, not only a fast developer machine and Wi-Fi.
- **SHOULD:** Prefer `transform` and `opacity` for animation; avoid repeated layout and paint work. Do not optimize blindly at the expense of maintainability.
- **WHEN APPLICABLE:** Set explicit budgets for JavaScript, images, fonts, and route payloads based on the product's device and network audience.

## 14. Reliability, security, and operational maturity

A production product must be trustworthy behind the interface too. These checks are part of the agent's audit, but do not attempt backend or infrastructure changes outside the task's scope or permissions.

- **MUST:** Never expose secrets, API keys, private tokens, service credentials, or privileged configuration in client bundles or committed files.
- **MUST:** Enforce authorization and input validation on the server. Hiding a button is not access control.
- **MUST:** Handle authentication expiry, session refresh, logout, and account switching without leaking cached user data.
- **MUST:** Avoid logging passwords, tokens, payment data, or sensitive personal data. Minimize collection and retention.
- **MUST:** Show safe, user-readable errors. Keep diagnostic details in protected logs, not the public interface.
- **SHOULD:** Use error boundaries or equivalent recovery boundaries for major UI regions. One failing widget should not necessarily blank the entire app.
- **SHOULD:** Provide retry behavior with backoff for transient failures; do not retry non-idempotent actions blindly.
- **SHOULD:** Make writes idempotent where possible and handle duplicate requests, race conditions, and stale updates.
- **SHOULD:** Include empty, loading, error, offline, and permission states in tests.
- **SHOULD:** Use structured logs and error monitoring with enough context to diagnose issues, while redacting sensitive fields.
- **SHOULD:** Provide health checks and deployment rollback paths for services where the task includes operations.
- **WHEN APPLICABLE:** Add audit history, export/delete controls, data retention settings, rate limits, abuse prevention, and privacy disclosures according to the product's risk.
