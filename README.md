# Embedding Atlas (Fork with Highlight Prop)

[![NPM Version](https://img.shields.io/npm/v/@dataelvisliang/embedding-atlas)](https://www.npmjs.com/package/@dataelvisliang/embedding-atlas)
[![PyPI - Version](https://img.shields.io/pypi/v/embedding-atlas)](https://pypi.org/project/embedding-atlas/)
[![Paper](https://img.shields.io/badge/paper-arXiv:2505.06386-b31b1b.svg)](https://arxiv.org/abs/2505.06386)
[![GitHub License](https://img.shields.io/github/license/apple/embedding-atlas)](./LICENSE)

> **This is a fork of [apple/embedding-atlas](https://github.com/apple/embedding-atlas) with programmatic highlight support.**
>
> **npm package:** `@dataelvisliang/embedding-atlas` (v0.15.0-highlight.2)
>
> **PR:** [#143](https://github.com/apple/embedding-atlas/pull/143) - Adds `highlight` prop for external point highlighting

---

## What's Different in This Fork

This fork adds a **`highlight` prop** that allows you to programmatically highlight specific points on the embedding visualization with orange circles (same visual treatment as built-in search).

```tsx
import { EmbeddingAtlas } from '@dataelvisliang/embedding-atlas/react';

// Highlight specific points by their row IDs
<EmbeddingAtlas
  highlight={[1, 2, 3, 4, 5]}  // Array of row IDs to highlight
  // ... other props
/>

// Clear highlight
<EmbeddingAtlas highlight={null} />
```

### Use Cases
- **AI/LLM Integration**: Highlight points returned by an AI agent's search queries
- **External Filters**: Show results from custom search or filter logic
- **Coordinated Views**: Link selections from other visualizations to the embedding map
- **Automated Workflows**: Programmatically direct user attention to specific data points

### Installation

```bash
npm install @dataelvisliang/embedding-atlas
```

### Upstream Compatibility

This fork tracks the official repository. Once [PR #143](https://github.com/apple/embedding-atlas/pull/143) is merged, you can switch back:

```bash
npm uninstall @dataelvisliang/embedding-atlas
npm install embedding-atlas
```

---

## Original README

Embedding Atlas is a tool that provides interactive visualizations for large embeddings. It allows you to visualize, cross-filter, and search embeddings and metadata.

**Features**

- 🏷️ **Automatic data clustering & labeling:**
  Interactively visualize and navigate overall data structure.

- 🫧 **Kernel density estimation & density contours:**
  Easily explore and distinguish between dense regions of data and outliers.

- 🧊 **Order-independent transparency:**
  Ensure clear, accurate rendering of overlapping points.

- 🔍 **Real-time search & nearest neighbors:**
  Find similar data to a given query or existing data point.

- 🚀 **WebGPU implementation (with WebGL 2 fallback):**
  Fast, smooth performance (up to few million points) with modern rendering stack.

- 📊 **Multi-coordinated views for metadata exploration:**
  Interactively link and filter data across metadata columns.

Please visit <https://apple.github.io/embedding-atlas> for a demo and documentation.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./packages/docs/assets/embedding-atlas-dark.png">
  <img alt="screenshot of Embedding Atlas" src="./packages/docs/assets/embedding-atlas-light.png">
</picture>

## Get started

To use Embedding Atlas with Python:

```bash
pip install embedding-atlas

embedding-atlas <your-dataset.parquet>
```

In addition to the command line tool, Embedding Atlas is also available as a Python Notebook (e.g., Jupyter) widget:

```python
from embedding_atlas.widget import EmbeddingAtlasWidget

# Show the Embedding Atlas widget for your data frame:
EmbeddingAtlasWidget(df)
```

Finally, components from Embedding Atlas are also available in an npm package:

```bash
npm install embedding-atlas
```

```js
import { EmbeddingAtlas, EmbeddingView, Table } from "embedding-atlas";

// or with React:
import { EmbeddingAtlas, EmbeddingView, Table } from "embedding-atlas/react";

// or Svelte:
import { EmbeddingAtlas, EmbeddingView, Table } from "embedding-atlas/svelte";
```

For more information, please visit <https://apple.github.io/embedding-atlas/overview.html>.

## BibTeX

For the Embedding Atlas tool:

```bibtex
@misc{ren2025embedding,
  title={Embedding Atlas: Low-Friction, Interactive Embedding Visualization},
  author={Donghao Ren and Fred Hohman and Halden Lin and Dominik Moritz},
  year={2025},
  eprint={2505.06386},
  archivePrefix={arXiv},
  primaryClass={cs.HC},
  url={https://arxiv.org/abs/2505.06386},
}
```

For the algorithm that automatically produces clusters and labels in the embedding view:

```bibtex
@misc{ren2025scalable,
  title={A Scalable Approach to Clustering Embedding Projections},
  author={Donghao Ren and Fred Hohman and Dominik Moritz},
  year={2025},
  eprint={2504.07285},
  archivePrefix={arXiv},
  primaryClass={cs.HC},
  url={https://arxiv.org/abs/2504.07285},
}
```

## Development

This repo contains multiple sub-packages:

Frontend:

- `packages/component`: The `EmbeddingView` and `EmbeddingViewMosaic` components.

- `packages/table`: The `Table` component.

- `packages/viewer`: The frontend application for visualizing embedding and other columns. It also provides the `EmbeddingAtlas` component that can be embedded in other applications.

- `packages/density-clustering`: The density clustering algorithm, written in Rust.

- `packages/umap-wasm`: An implementation of UMAP algorithm in WebAssembly (with the [umappp](https://github.com/libscran/umappp) C++ library).

- `packages/embedding-atlas`: The `embedding-atlas` package that get published. It imports all of the above and exposes their API in a single package.

Python:

- `packages/backend`: A Python package named `embedding-atlas` that provides the `embedding-atlas` command line tool.

Documentation:

- `packages/docs`: The documentation website.

For more information, please visit <https://apple.github.io/embedding-atlas/develop.html>.

## License

This code is released under the [`MIT license`](LICENSE).
