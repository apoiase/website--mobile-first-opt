# Graph Report - .  (2026-07-18)

## Corpus Check
- Corpus is ~2,606 words - fits in a single context window. You may not need a graph.

## Summary
- 60 nodes · 57 edges · 10 communities (5 shown, 5 thin omitted)
- Extraction: 96% EXTRACTED · 4% INFERRED · 0% AMBIGUOUS · INFERRED: 2 edges (avg confidence: 0.7)
- Token cost: 1,200 input · 0 output

## Community Hubs (Navigation)
- TypeScript compiler options
- Pipeline de deploy (push main)
- Integracao Plasmic (catch-all + host)
- Dependencias runtime
- DevDependencies
- API route boilerplate
- tsconfig include/exclude
- ESLint config
- Next config
- next-env.d.ts gerado

## God Nodes (most connected - your core abstractions)
1. `compilerOptions` - 15 edges
2. `scripts` - 5 edges
3. `PLASMIC` - 5 edges
4. `build` - 2 edges
5. `@plasmicapp/loader-nextjs` - 2 edges
6. `getStaticProps()` - 2 edges
7. `getStaticPaths()` - 2 edges
8. `create-plasmic-app boilerplate docs` - 2 edges
9. `extends` - 1 edges
10. `NOTE: This file should not be edited` - 1 edges

## Surprising Connections (you probably didn't know these)
- `Vercel logo asset (unused boilerplate)` --conceptually_related_to--> `create-plasmic-app boilerplate docs`  [INFERRED]
  public/vercel.svg → README.md
- `Push-to-main build/deploy pipeline` --references--> `build`  [EXTRACTED]
  .github/workflows/plasmic-push.yml → package.json
- `create-plasmic-app boilerplate docs` --references--> `@plasmicapp/loader-nextjs`  [EXTRACTED]
  README.md → package.json
- `getStaticProps()` --references--> `PLASMIC`  [EXTRACTED]
  pages/[[...catchall]].tsx → plasmic-init.ts
- `getStaticPaths()` --references--> `PLASMIC`  [EXTRACTED]
  pages/[[...catchall]].tsx → plasmic-init.ts

## Import Cycles
- None detected.

## Communities (10 total, 5 thin omitted)

### Community 0 - "TypeScript compiler options"
Cohesion: 0.13
Nodes (15): compilerOptions, allowJs, esModuleInterop, forceConsistentCasingInFileNames, incremental, isolatedModules, jsx, lib (+7 more)

### Community 1 - "Pipeline de deploy (push main)"
Cohesion: 0.20
Nodes (9): Push-to-main build/deploy pipeline, name, private, scripts, build, dev, lint, start (+1 more)

### Community 2 - "Integracao Plasmic (catch-all + host)"
Cohesion: 0.33
Nodes (4): Plasmic Studio sync/build/PR pipeline, getStaticPaths(), getStaticProps(), PLASMIC

### Community 3 - "Dependencias runtime"
Cohesion: 0.29
Nodes (7): dependencies, next, @plasmicapp/loader-nextjs, react, react-dom, Vercel logo asset (unused boilerplate), create-plasmic-app boilerplate docs

### Community 4 - "DevDependencies"
Cohesion: 0.29
Nodes (7): devDependencies, eslint, eslint-config-next, @types/node, @types/react, @types/react-dom, typescript

## Knowledge Gaps
- **37 isolated node(s):** `extends`, `nextConfig`, `name`, `version`, `private` (+32 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **5 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `compilerOptions` connect `TypeScript compiler options` to `tsconfig include/exclude`?**
  _High betweenness centrality (0.078) - this node is a cross-community bridge._
- **Why does `devDependencies` connect `DevDependencies` to `Pipeline de deploy (push main)`?**
  _High betweenness centrality (0.068) - this node is a cross-community bridge._
- **Why does `dependencies` connect `Dependencias runtime` to `Pipeline de deploy (push main)`?**
  _High betweenness centrality (0.067) - this node is a cross-community bridge._
- **What connects `extends`, `NOTE: This file should not be edited`, `nextConfig` to the rest of the system?**
  _38 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `TypeScript compiler options` be split into smaller, more focused modules?**
  _Cohesion score 0.13333333333333333 - nodes in this community are weakly interconnected._