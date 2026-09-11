# BM25 Indexer

A high-performance, interactive full-text search tool that uses the BM25 ranking algorithm to index and search through text files in real-time. Built with C++20 for maximum speed and efficiency.

## Why BM25 Indexer?

BM25 is a probabilistic information retrieval function used in search engines to rank documents based on their relevance to a search query. This tool brings the power of BM25 to your local filesystem, allowing you to:

- **Instantly search** through thousands of text files
- **Get ranked results** based on relevance scores
- **Use natural language queries** with intelligent preprocessing
- **Choose between speed and accuracy** with multiple optimization modes
- **Navigate results interactively** with a terminal UI

Perfect for developers, researchers, and anyone who needs to quickly find information across large codebases, documentation, or text collections.

## Features

- **BM25 Ranking Algorithm**: Industry-standard relevance scoring for accurate search results
- **Stopword Removal**: Filter out common words (non-aggressive and aggressive modes)
- **Snowball Stemming**: Reliable word stemming for better matching (Porter algorithm)
- **Lancaster Stemming**: Fast, aggressive stemming for quick searches
- **Reactive TUI**: Interactive terminal interface with real-time search
- **Multiple File Formats**: Supports 70+ file extensions (code, docs, configs, etc.)
- **Optimization Modes**: Choose between speed and accuracy based on your needs
- **Recursive Directory Traversal**: Index entire directory trees automatically

## Dependencies

### Build Requirements
- **C++20 compatible compiler**: g++ (recommended), clang, or MSVC
- **Make**: For building the project
- **CMake** (optional): Alternative build system

### System Requirements
- Linux/Unix-like operating system
- POSIX-compliant terminal for TUI functionality

## Installation

### Option 1: Build and Run Locally

1. Clone the repository:
```bash
git clone https://github.com/IhitplayzYT/BM_25-indexer.git
cd BM_25-indexer
```

2. Build the executable:
```bash
make
```

3. Run the executable:
```bash
./BM25_indexer -h
```

### Option 2: Install System-Wide

1. Clone and navigate to the repository:
```bash
git clone https://github.com/IhitplayzYT/BM_25-indexer.git
cd BM_25-indexer
```

2. Install to `/usr/bin` (requires sudo):
```bash
sudo make install
```

3. Restart your shell or source your bashrc:
```bash
source ~/.bashrc
```

4. Run from anywhere:
```bash
BM25_indexer /path/to/search
```

### Option 3: Uninstall

1. Navigate to the repository:
```bash
cd BM_25-indexer
```

2. Remove the system-wide installation:
```bash
sudo make uninstall
```

3. Restart your shell:
```bash
source ~/.bashrc
```

## Usage

### Basic Syntax

```bash
BM25_indexer [OPTIONS] <FILEPATH>
```

### Options

- `-h` or `-H`: Show help message
- `-OPTIMISE=<mode>` or `-O<mode>`: Set optimization mode

### Optimization Modes

| Mode | Stopword Removal | Stemming | Description |
|------|------------------|----------|-------------|
| `0` | Non-Aggressive | Snowball | Reliable search (default) |
| `1` | Non-Aggressive | Lancaster | Quick search |
| `2` | Aggressive | Snowball | Reliable search with more filtering |
| `3` | Aggressive | Lancaster | Quick search with more filtering |
| `s` | None | Snowball | No stopword removal |
| `f` | Non-Aggressive | None | Stopword removal only |
| `x` | None | None | Raw text search (fastest) |

### Examples

1. **Search a directory with default settings (Mode 0):**
```bash
./BM25_indexer /home/user/documents
```

2. **Search with aggressive filtering for more precise results:**
```bash
./BM25_indexer -OPTIMISE=2 /home/user/code
```

3. **Quick search using Lancaster stemming:**
```bash
./BM25_indexer -O1 /var/log
```

4. **Raw text search (no preprocessing):**
```bash
./BM25_indexer -Ox /home/user/notes
```

5. **Search code with Snowball stemming only:**
```bash
./BM25_indexer -Os /home/user/projects
```

### Interactive TUI Controls

Once the search interface launches:

- **Type**: Enter your search query (results update in real-time)
- **↑/↓ Arrow Keys**: Navigate through results
- **Enter**: Select and display the chosen file path
- **Backspace**: Delete characters from query
- **ESC**: Exit the search interface

## How It Works

1. **Indexing**: The tool recursively scans the specified directory, reading all supported file types
2. **Preprocessing**: Text is lowercased, punctuation removed, and optionally filtered/stemmed
3. **BM25 Scoring**: Documents are scored based on term frequency, document frequency, and length normalization
4. **Ranking**: Results are sorted by relevance score in descending order
5. **Interactive Search**: As you type, the query is processed and results are updated instantly

## Supported File Types

The indexer supports 70+ file extensions including:
- **Text files**: .txt, .md, .log, .csv, .json, .xml
- **Code files**: .cpp, .py, .js, .rs, .go, .java, .c, .h
- **Config files**: .yaml, .toml, .ini, .cfg
- **Documentation**: .rst, .adoc, .tex
- **And many more** (see `includes/utility.h` for complete list)

## Architecture

The project is structured as follows:

- `main.cpp`: Entry point and file processing logic
- `bm25.cpp`: BM25 scoring algorithm implementation
- `Stemmer.cpp`: Snowball and Lancaster stemming algorithms
- `stopwords.cpp`: Stopword filtering with aggressive/non-aggressive modes
- `utility.cpp`: Text preprocessing and utility functions
- `fzf_tui.cpp`: Terminal UI implementation
- `errors.cpp`: Error handling and debugging utilities
- `includes/`: Header files for all modules

## Performance

- **Indexing**: Processes thousands of files in seconds
- **Search**: Sub-millisecond query response times
- **Memory**: Uses polymorphic allocators for efficient memory management
- **Scalability**: Handles large codebases and document collections

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## Author

Built by IhitplayzYT

