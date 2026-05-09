# Local RAG, Vector Search and Knowledge Graph Enhancement

**Project Title:** Advanced Retrieval-Augmented Generation Pipeline with Knowledge Graph Enhancement

**Authors**
- Mashudu Maboko
- Supervised by: Gift Malebo Maboko — MSc Engineering: Artificial Intelligence; Data Scientist / AI and Data Engineering Practitioner

---

## Project Overview
This repository contains a co-authored software design project for an end-to-end Retrieval-Augmented Generation (RAG) system with knowledge graph enhancement. The implementation covers document ingestion, vector search, graph-based retrieval, local LLM inference, and quantitative evaluation in a four-phase architecture.

**Core technical facts**
- **Corpus:** 515 Wikipedia articles
- **Chunking:** 800-character chunks with 200-character overlap
- **Indexed chunks:** 10,857
- **Embeddings:** all-MiniLM-L6-v2 (384 dimensions)
- **Vector database:** ChromaDB
- **LLM:** Ollama with `gemma3:1b`
- **Graph library:** NetworkX
- **KG contribution:** contextual chunks increased from 3 to 5 (~+67%)

**Corpus note:** Some notebook outputs show 505 documents after a quality filter removes very short files. The final cleaned corpus/report references the full set of 515 articles.

---

## Why This Project Matters
This project focuses on practical AI engineering and data engineering: building a local RAG system, implementing vector search, enhancing retrieval with knowledge graphs, running local LLM inference, and evaluating quality improvements using measurable metrics and prompts that handle unknowns responsibly.

---

## System Architecture (4 Phases)
1. **Phase 1: Foundation and Navigation Graph**
   - Document ingestion, metadata tracking, navigation graph construction, and quality filtering
2. **Phase 2: Vector RAG Pipeline**
   - RecursiveCharacterTextSplitter, ChromaDB indexing, all-MiniLM-L6-v2 embeddings, Ollama inference
3. **Phase 3: Knowledge Graph Enhancement**
   - Enhanced Regex entity extraction and NetworkX entity co-occurrence graphs
4. **Phase 4: Quality Improvements and Evaluation**
   - Improved prompts, balanced LLM parameters, smart post-processing, query coverage checks, and evaluation

---

## Key Results and Evaluation

| Metric | Result | Target | Status |
|--------|--------|--------|--------|
| Answer variety (Basic RAG) | 42.3% similarity | <75% | Pass |
| Answer variety (KG-enhanced RAG) | 60.1% similarity | <75% | Pass |
| KG contribution | 3 → 5 chunks | +67% | Improved |
| Unknown detection | Missing evidence acknowledged | Must detect | Pass |

**Example query:** “Tell me about Andrea Palladio and his love for money”  
**Observed behavior:** The improved system answers supported facts about Palladio and explicitly acknowledges that the “love for money” claim is not supported by retrieved evidence.

---

## Technology Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Vector DB** | ChromaDB | Local persistent vector storage |
| **Embeddings** | all-MiniLM-L6-v2 | 384-dim sentence embeddings |
| **LLM** | Ollama + `gemma3:1b` | Local inference |
| **Framework** | LangChain | Text splitting and RAG utilities |
| **Graph** | NetworkX | Entity relationship graphs |
| **NER** | Enhanced Regex | Lightweight entity extraction |

---

## Key Skills 
- Python
- RAG pipeline design
- Vector databases
- Embeddings
- Knowledge graphs
- NetworkX
- ChromaDB
- LangChain
- Ollama / local LLMs
- Evaluation and metrics
- Technical documentation

---


## Project Structure
```
MyRAG/
├── README.md                               # Project overview, setup, usage, and results
├── LICENSE                                 # MIT license
├── requirements.txt                        # Python dependencies
├── metadata.csv                            # Document navigation relationships
├── rag_architecture.png                    # System architecture diagram
├── RAG_Pipeline_Report.pdf                 # Final technical report
├── RAG_Pipeline_Complete_Story.ipynb       # Main implementation notebook
├── documents/                              # Wikipedia article corpus (.txt)
├── src/                                    # Python package structure for modularization
├── tests/                                  # Test package placeholder
└── .gitignore                              # Local artifact and environment exclusions
```

---

## Quick Start

### Prerequisites
1. **Python 3.12+** (tested on 3.12.4)
2. **Ollama** installed and running  
   - Download: https://ollama.ai/download  
   - Pull model: `ollama pull gemma3:1b`

### Installation
```bash
cd MyRAG
python -m venv rag_env

# Activate (Windows)
rag_env\Scripts\activate

# Activate (macOS/Linux)
# source rag_env/bin/activate

pip install -r requirements.txt
python -c "import nltk; nltk.download('punkt'); nltk.download('punkt_tab')"
```

### Running the Notebook
```bash
jupyter notebook RAG_Pipeline_Complete_Story.ipynb
```

**Execution:** Run all cells sequentially  
**Expected runtime:** 5–10 minutes (excluding initial model download)

---

## Usage Examples

### Basic Query
```python
query = "Tell me about coffee production methods"
answer = answer_question(query, top_k=10)
print(answer)
```

### KG-Enhanced Query
```python
query = "Tell me about coffee production methods"
answer = answer_question_with_graph_improved(query, top_k_vector=10, top_k_kg=5)
print(answer)
```

### Compare Approaches
```python
# Use the evaluation cells near the end of the notebook
# Compares basic vs KG-enhanced results and reports metrics
```

---

## Troubleshooting

### Issue: Ollama connection failed
```bash
ollama list
ollama serve
ollama pull gemma3:1b
```

### Issue: ChromaDB errors
Remove the local database and rebuild in Phase 2.
```bash
# macOS/Linux
rm -rf chroma_db/

# Windows PowerShell
Remove-Item -Recurse -Force chroma_db\
```

### Issue: NLTK download errors
```python
import nltk
nltk.download('punkt')
nltk.download('punkt_tab')
```

---

## Future Work
1. Larger models for higher answer quality
2. spaCy NER for improved entity extraction
3. PageRank or centrality measures for entity importance
4. Expert evaluation dataset for more rigorous benchmarking
5. Streamlit dashboard for interactive exploration

---



---

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
