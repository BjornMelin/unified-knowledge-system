# Architecture: Unified Knowledge Management System

This document provides a detailed overview of the Unified Knowledge Management System architecture, explaining how each component works together to create a comprehensive knowledge access solution.

## System Architecture Overview

Our system consists of six distinct layers, each with a specific responsibility in the knowledge flow:

1. **Web Content Acquisition Layer**: Responsible for gathering information from multiple sources
2. **Knowledge Processing Layer**: Processes raw content into structured knowledge
3. **Knowledge Storage Layer**: Stores processed knowledge in specialized databases
4. **MCP Server Layer**: Exposes knowledge via standardized Machine Comprehension Protocol
5. **Integration Layer**: Unifies access across different knowledge sources
6. **Client Layer**: End-user applications that consume unified knowledge

## Detailed Layer Descriptions

### 1. Web Content Acquisition Layer

This layer is responsible for acquiring content from various sources:

**DevDocs Integration**
- Free and open-source documentation crawler (364 GitHub stars)
- Processes up to 1000 pages/minute
- Focuses on technical documentation, API references, and developer resources
- Supports incremental crawling and content change detection

**Firecrawl Integration**
- Commercial web crawler ($16/month)
- Processes approximately 20 pages/minute
- Handles general web content, blogs, news sites, and research papers
- Supports JavaScript rendering for dynamic content
- Provides advanced filtering and content extraction capabilities

### 2. Knowledge Processing Layer

This layer processes raw content into structured, searchable knowledge:

**Text Chunking**
- Divides documents into semantically meaningful chunks
- Uses 512 token chunks with 50 token overlap for context preservation
- Preserves document structure and relationships between chunks
- Implements adaptive chunking based on content type

**Vector Embedding**
- Converts text chunks into high-dimensional vector representations
- Uses Sentence Transformers (all-MiniLM-L6-v2) with 768-dimension vectors
- Optimized for semantic similarity across technical and general content
- Supports incremental embedding updates

**Entity Extraction**
- Identifies entities (concepts, people, organizations, code elements) in content
- Detects relationships between entities
- Creates knowledge graph structure from unstructured text
- Preserves source attribution for provenance

### 3. Knowledge Storage Layer

This layer stores processed knowledge in specialized databases optimized for different query patterns:

**Structured Documents Store**
- Stores original documents and chunked content in structured format (JSON/Markdown)
- Preserves document hierarchy and metadata
- Enables direct document retrieval and browsing
- Supports versioning and change tracking

**Qdrant Vector Database**
- High-performance vector similarity search
- Achieves 626 QPS (queries per second) at 99.5% recall
- Supports filtering by metadata
- Enables efficient semantic search across all content
- Implements optimized HNSW (Hierarchical Navigable Small World) algorithm

**Knowledge Graph Database**
- Stores entities and relationships
- Enables graph traversal queries
- Supports relationship-based knowledge navigation
- Preserves domain-specific knowledge structures

**Obsidian Vault**
- Stores personal knowledge and notes
- Provides bidirectional linking capabilities
- Allows visual graph exploration
- Supports personal knowledge augmentation

### 4. MCP Server Layer

This layer provides standardized access to different knowledge sources via the Machine Comprehension Protocol:

**DevDocs MCP**
- Exposes technical documentation via stdio transport
- Implements document retrieval and search capabilities
- Supports structured queries for APIs and code elements

**Firecrawl MCP**
- Exposes web content via HTTP+SSE transport
- Implements content retrieval and search capabilities
- Supports filtering by source, date, and relevance

**Qdrant MCP**
- Exposes vector search capabilities via stdio transport
- Implements semantic similarity search
- Supports hybrid search with metadata filtering

**Knowledge Graph MCP**
- Exposes knowledge graph via stdio transport
- Implements entity and relationship queries
- Supports graph traversal operations

### 5. Integration Layer

This layer unifies access to different knowledge sources:

**Unified Search Engine**
- Combines results from multiple knowledge sources
- Implements intelligent query routing based on query type
- Merges and ranks results by relevance
- Preserves source attribution
- Handles different query modalities (keyword, semantic, graph)

**Supergateway**
- Converts between different transport protocols (stdio ↔ SSE)
- Provides unified access point for clients
- Handles authentication and request routing
- Enables remote access for standalone applications

### 6. Client Layer

This layer consists of end-user applications that consume unified knowledge:

**Claude Desktop**
- AI assistant with access to unified knowledge
- Interacts with knowledge via MCP
- Provides natural language interface to knowledge

**Cursor**
- AI-enhanced code editor
- Accesses technical documentation and code examples
- Integrates knowledge into development workflow

**Roo Code**
- AI coding assistant
- Leverages unified knowledge for code generation and problem-solving
- Provides contextual assistance based on project content

## Data Flow

1. Content is acquired from web sources via DevDocs and Firecrawl
2. Raw content is processed into structured knowledge (chunks, vectors, entities)
3. Processed knowledge is stored in specialized databases
4. MCP servers expose knowledge via standardized interfaces
5. Integration layer unifies access across knowledge sources
6. Clients consume unified knowledge via Supergateway

## Performance Considerations

- Qdrant vector database provides 626 QPS at 99.5% recall
- DevDocs processes up to 1000 pages/minute for technical documentation
- Firecrawl processes approximately 20 pages/minute for general web content
- Vector dimensions are optimized at 768 to balance accuracy and performance
- Knowledge Graph queries are optimized with proper indexing
- Transport protocol conversion adds minimal overhead (<5ms per request)

## Security Architecture

- Authentication at the Integration Layer
- Transport encryption for all network communication
- Access control for knowledge sources
- Proper handling of sensitive information
- Regular security scanning and updates

## Deployment Architecture

The system can be deployed in various configurations:

- **Local Deployment**: All components run on local machine
- **Server Deployment**: Components run on dedicated server
- **Hybrid Deployment**: Critical components on server, clients on local machines
- **Containerized Deployment**: Components in Docker containers for easy scaling

## Extensibility

The architecture is designed for extensibility:

- New knowledge sources can be added at the Acquisition Layer
- New processing methods can be incorporated in the Processing Layer
- Additional storage mechanisms can be integrated in the Storage Layer
- New MCP servers can be added to support additional knowledge sources
- The Integration Layer can adapt to new knowledge types
- Additional clients can be supported via the standardized interface

## Implementation Considerations

- Consistent use of configuration files across all components
- Comprehensive logging and monitoring
- Error handling and recovery mechanisms
- Clear documentation for all interfaces
- Automated testing for all components
