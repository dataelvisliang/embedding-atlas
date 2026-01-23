# @dataelvisliang/embedding-atlas

Fork of [embedding-atlas](https://github.com/apple/embedding-atlas) with **highlight prop support** for programmatic point highlighting.

## Installation

```bash
npm install @dataelvisliang/embedding-atlas
```

## What's Different

This fork adds a `highlight` prop that allows you to programmatically highlight specific points on the embedding visualization with orange circles (same visual treatment as the built-in search).

### New Feature: `highlight` prop

```tsx
import { EmbeddingAtlas } from '@dataelvisliang/embedding-atlas/react';

// Highlight specific points by their row IDs
<EmbeddingAtlas
  highlight={[1, 2, 3, 4, 5]}  // Array of row IDs to highlight
  // ... other props
/>

// Clear highlight
<EmbeddingAtlas
  highlight={null}
  // ... other props
/>
```

### Use Cases

- **AI/LLM Integration**: Highlight points returned by an AI agent's search queries
- **External Filters**: Show results from custom search or filter logic
- **Coordinated Views**: Link selections from other visualizations to the embedding map
- **Automated Workflows**: Programmatically direct user attention to specific data points

## Usage

```tsx
import { EmbeddingAtlas } from '@dataelvisliang/embedding-atlas/react';
import { coordinator, wasmConnector } from '@uwdata/mosaic-core';

// Initialize coordinator
const c = coordinator();
await c.databaseConnector(await wasmConnector());
await c.exec(`CREATE TABLE data AS SELECT * FROM 'data.parquet'`);

// Use the component
<EmbeddingAtlas
  coordinator={c}
  data={{
    table: "data",
    id: "__row_index__",
    text: "description",
    projection: { x: "x", y: "y" },
    neighbors: "neighbors"
  }}
  highlight={highlightedIds}  // NEW: programmatic highlighting
/>
```

## Upstream Compatibility

This fork tracks the official [apple/embedding-atlas](https://github.com/apple/embedding-atlas) repository. The highlight feature is proposed in [PR #143](https://github.com/apple/embedding-atlas/pull/143).

Once the PR is merged upstream, you can switch back to the official package:

```bash
npm uninstall @dataelvisliang/embedding-atlas
npm install embedding-atlas
```

## Original Documentation

- Documentation: https://apple.github.io/embedding-atlas
- GitHub: https://github.com/apple/embedding-atlas

## License

MIT (same as upstream)