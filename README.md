# Smart Memory

A lightweight semantic memory system for AI assistants. Stores notes with vector embeddings for context retrieval.

## Features

- 🔍 **Semantic search** - Find relevant memories by meaning, not just keywords
- 🤖 **No AI APIs** - Uses local TF-IDF vectorization (works offline)
- 💾 **JSONL storage** - Human-readable, append-only format
- ⚡ **Fast search** - Cosine similarity with pre-computed vectors
- 🏷️ **Auto-timestamped** - Every memory tracked with creation time

## Installation

```bash
cd projects/smart-memory
npm install  # No dependencies to install!
```

## Usage

```bash
# Add a memory
node memory.js add "User prefers dark mode in all apps"

# Search memories by meaning
node memory.js search "user preferences"

# List recent memories
node memory.js list
```

## How It Works

1. **Tokenization** - Text is split into words (lowercased, punctuation removed)
2. **Vectorization** - Each memory is converted to a TF-IDF-like vector
3. **Storage** - Memories saved to `memories.jsonl` (one per line)
4. **Search** - Query vectorized and compared using cosine similarity
5. **Ranking** - Results sorted by similarity score (0-100%)

## File Structure

```
smart-memory/
├── memory.js       # Main CLI
├── memories.jsonl  # Your memory storage
├── package.json    # No dependencies!
└── README.md       # This file
```

## Example

```bash
$ node memory.js add "Docker is useful for containerization"
✓ Saved memory kx8j2s

$ node memory.js add "Kubernetes orchestrates containers"
✓ Saved memory kx8j3t

$ node memory.js search "container technology"
Found 2 relevant memories:

1. [87.3%] Docker is useful for containerization
   2/16/2026, 10:30:00 AM

2. [82.1%] Kubernetes orchestrates containers
   2/16/2026, 10:31:00 AM
```

## Tech Stack

- Pure Node.js (no dependencies)
- Cosine similarity for ranking
- JSONL for storage

## License

MIT
