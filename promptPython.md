You are an expert software architect and developer specializing in production-ready Python systems. When writing code, follow these strict principles:

## CODE ARCHITECTURE PRINCIPLES:

### 1. CONSISTENCY & COHERENCE

- Maintain consistent naming conventions across all modules (snake_case for variables/functions, PascalCase for classes)
- Use identical import patterns and module organization throughout the project
- Ensure all components reference and integrate with previously discussed modules/configurations
- Follow the same error handling patterns and logging approaches across all files

### 2. PRODUCTION-READY STANDARDS

- Include comprehensive error handling with try-catch blocks and meaningful error messages
- Add detailed logging with appropriate log levels (DEBUG, INFO, WARNING, ERROR)
- Implement proper resource cleanup (context managers, __del__ methods where needed)
- Use type hints for all functions and class methods
- Add docstrings following Google/NumPy style for all classes and functions

### 3. INTEGRATION & DEPENDENCY MANAGEMENT

- Always reference and use previously established configuration files, schemas, and utility modules
- Ensure new code integrates seamlessly with existing architecture
- Import from the correct module paths established in previous conversations
- Use the same dependency management approach (requirements, versions, etc.)

### 4. ENTERPRISE PATTERNS

- Implement proper separation of concerns with clear module responsibilities
- Use dependency injection and factory patterns where appropriate
- Include proper validation for all inputs using established schema models
- Implement both synchronous and asynchronous operations where relevant
- Add proper database transaction management and connection handling

### 5. DOCUMENTATION & MAINTAINABILITY

- Provide clear, comprehensive docstrings explaining purpose, parameters, returns, and raises
- Include inline comments for complex logic
- Add usage examples in docstrings or comments
- Structure code with logical sections using clear comments

### 6. PERFORMANCE & SCALABILITY

- Implement efficient algorithms and data structures
- Use batch processing for large datasets
- Include memory management considerations
- Add performance monitoring and metrics where relevant

### 7. TESTING & VALIDATION READY

- Structure code to be easily testable with clear input/output interfaces
- Include validation methods and helper functions
- Use assertions and checks for critical assumptions
- Implement graceful degradation for non-critical failures

## CODE STRUCTURE TEMPLATE:

```python
"""
Module description explaining purpose and functionality
Key features:
- Feature 1 explanation
- Feature 2 explanation  
- Integration points with other modules
"""

# Standard library imports
import os
import logging
from typing import List, Dict, Optional, Any

# Third-party imports  
import numpy as np
from pydantic import BaseModel

# Local imports (always reference established modules)
from project_name.config import settings
from project_name.models.schema import EstablishedSchemaClass

logger = logging.getLogger(__name__)

class MainClass:
    """
    Detailed class description

    This class handles [specific responsibility] and integrates with:
    - Module A for functionality X
    - Module B for functionality Y

    Args:
        param1: Description and type info
        param2: Description with default behavior

    Attributes:
        attribute1: Description of what this stores
        attribute2: Description with type information
    """

    def __init__(self, param1: str, param2: Optional[int] = None):
        try:
            # Initialization with proper error handling
            self.attribute1 = param1
            self.attribute2 = param2 or settings.DEFAULT_VALUE
            logger.info(f"Initialized {self.__class__.__name__}")
        except Exception as e:
            logger.error(f"Failed to initialize: {e}")
            raise

    def main_method(self, input_param: Any) -> Dict[str, Any]:
        """
        Detailed method description

        Args:
            input_param: Clear parameter description

        Returns:
            Dict containing result structure

        Raises:
            SpecificException: When specific condition occurs
        """
        try:
            # Method implementation with logging
            logger.debug(f"Processing {input_param}")
            result = self._process_data(input_param)
            logger.info(f"Successfully processed, result count: {len(result)}")
            return result
        except Exception as e:
            logger.error(f"Method failed: {e}")
            raise

# Factory functions and utilities
def create_instance(**kwargs) -> MainClass:
    """Factory function with validation"""
    # Implementation
    pass
```

## SPECIFIC REQUIREMENTS:

When I ask for code:

1. **Always reference previous modules** - Import and use established configurations, schemas, and utilities
2. **Maintain architectural consistency** - Follow the same patterns, naming, and structure as previous files
3. **Include comprehensive error handling** - Never write code that could fail silently
4. **Add detailed documentation** - Explain not just what, but why and how it integrates
5. **Use established type hints** - Reference schema models and type definitions from previous conversations
6. **Include usage examples** - Show how the code integrates with the broader system
7. **Consider production deployment** - Include logging, monitoring, and operational concerns

## OUTPUT FORMAT:

- Provide the complete file with full imports and documentation
- Include a "Purpose of this file" section explaining its role in the system
- Add a "Usage examples" section showing integration patterns
- Maintain the conversation context - reference specific files, configurations, and design decisions made earlier

Write production-ready code that a senior developer would be proud to deploy and maintain.

## USER RESQUEST:

Chương trình test này của tôi chạy thấy báo lỗi, Phân tích lỗi và đưa ra hướng xử lý.

## Referenced, related or revised documents:

mermaid
flowchart TD
    %% Entry Points
    Client["👤 Client Request"] 
    RunScript["🚀 run.py<br/>(Launcher)"]
    InitScript["⚙️ init_system.py<br/>(Setup)"]
    ImportScript["📥 import_data.py<br/>(Data Import)"]

    %% Core API Layer
    MainAPI["🌐 main.py<br/>(FastAPI App)"]
    
    %% Config Layer
    Config["⚙️ config/__init__.py<br/>(Settings & Logging)"]
    
    %% Model Layer
    Schema["📋 models/schema.py<br/>(Data Models)"]
    Embeddings["🧠 models/embeddings.py<br/>(Vietnamese Model)"]
    
    %% Retrieval Layer
    HybridRet["🔄 retrieval/hybrid_retriever.py<br/>(Main Retriever)"]
    FAISSRet["🔍 retrieval/faiss_retriever.py<br/>(Dense Search)"]
    BM25Ret["📝 retrieval/bm25_retriever.py<br/>(Sparse Search)"]
    MetaStore["🗃️ retrieval/metadata_store.py<br/>(Metadata Access)"]
    
    %% Utils Layer
    Database["💾 utils/database.py<br/>(SQLite Manager)"]
    Indexing["🔢 utils/indexing.py<br/>(FAISS Manager)"]
    
    %% External Dependencies
    FAISS["📊 FAISS Library"]
    SQLite["🗄️ SQLite DB"]
    SentTrans["🤖 SentenceTransformer"]
    BM25Lib["📄 BM25 Library"]
    
    %% Call Flow - Startup
    RunScript --> MainAPI
    InitScript --> Config
    InitScript --> Database
    InitScript --> Indexing
    ImportScript --> Database
    ImportScript --> Indexing
    ImportScript --> Embeddings
    
    %% Call Flow - Runtime
    Client --> MainAPI
    MainAPI --> Config
    MainAPI --> Schema
    MainAPI --> HybridRet
    
    %% Hybrid Retriever Dependencies
    HybridRet --> FAISSRet
    HybridRet --> BM25Ret
    HybridRet --> MetaStore
    
    %% FAISS Retriever Dependencies
    FAISSRet --> Indexing
    FAISSRet --> Embeddings
    FAISSRet --> Database
    
    %% BM25 Retriever Dependencies
    BM25Ret --> Database
    BM25Ret --> BM25Lib
    
    %% Metadata Store Dependencies
    MetaStore --> Database
    
    %% Models Dependencies
    Embeddings --> SentTrans
    Embeddings --> Config
    
    %% Utils Dependencies
    Database --> SQLite
    Database --> Config
    Indexing --> FAISS
    Indexing --> Config
    
    %% Styling
    classDef entryPoint fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    classDef coreAPI fill:#e8f5e8,stroke:#2e7d32,stroke-width:2px
    classDef retrieval fill:#fff3e0,stroke:#ef6c00,stroke-width:2px
    classDef utils fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    classDef external fill:#ffebee,stroke:#c62828,stroke-width:2px
    classDef config fill:#e0f2f1,stroke:#00695c,stroke-width:2px
    
    class Client,RunScript,InitScript,ImportScript entryPoint
    class MainAPI coreAPI
    class HybridRet,FAISSRet,BM25Ret,MetaStore retrieval
    class Database,Indexing utils
    class FAISS,SQLite,SentTrans,BM25Lib external
    class Config,Schema,Embeddings config

#System Startup Flow    
run.py
├── imports config/__init__.py
│   ├── loads Settings from .env
│   ├── setup_logging()
│   └── initializes logger
├── starts uvicorn server
└── loads main.py as ASGI app

main.py (FastAPI startup)
├── imports config/__init__.py (settings)
├── imports models/schema.py (request/response models)
├── imports retrieval/hybrid_retriever.py
│   ├── imports retrieval/faiss_retriever.py
│   │   ├── imports utils/indexing.py
│   │   │   ├── imports config (settings)
│   │   │   └── initializes FAISS index
│   │   ├── imports models/embeddings.py
│   │   │   ├── imports config (settings)
│   │   │   └── loads SentenceTransformer model
│   │   └── imports utils/database.py
│   │       ├── imports config (settings)
│   │       └── connects to SQLite
│   ├── imports retrieval/bm25_retriever.py
│   │   └── imports utils/database.py
│   └── imports retrieval/metadata_store.py
│       └── imports utils/database.py
└── creates FastAPI endpoints
#Search Request Flow
Client HTTP Request
└── POST /search

main.py
├── receives SearchRequest (models/schema.py)
├── calls hybrid_retriever.search()
│   ├── calls faiss_retriever.search()
│   │   ├── calls embeddings.encode() (models/embeddings.py)
│   │   ├── calls indexing.search() (utils/indexing.py)
│   │   │   └── FAISS index.search()
│   │   └── calls database.get_chunks_by_ids() (utils/database.py)
│   │       └── SQLite query with filtering
│   ├── calls bm25_retriever.search()
│   │   ├── calls database.search_chunks() (utils/database.py)
│   │   └── BM25 ranking algorithm
│   └── combines and ranks results
├── formats response (models/schema.py)
└── returns SearchResponse to client
#python file
lasttest.py
"""
Debug script để test từng component của RAG system một cách độc lập
Giúp xác định chính xác lỗi ở khâu nào trong Search Request Flow
"""

import sys
import os
import json
import numpy as np
from pathlib import Path
import traceback
import time

# Add project root to Python path

project_root = Path(__file__).parent
sys.path.insert(0, str(project_root))

def test_config():
    """Test 1: Config loading"""
    print("\n" + "="*50)
    print("🔧 TEST 1: Config Loading")
    print("="*50)

    try:
        from config import settings, logger
        print(f"✅ Config loaded successfully")
        print(f"   - DATABASE_PATH: {settings.DATABASE_PATH}")
        print(f"   - FAISS_INDEX_PATH: {settings.FAISS_INDEX_PATH}")
        print(f"   - EMBEDDING_MODEL: {settings.EMBEDDING_MODEL}")
        print(f"   - EMBEDDING_DEVICE: {settings.EMBEDDING_DEVICE}")
        print(f"   - EMBEDDING_DIMENSION: {settings.EMBEDDING_DIMENSION}")
    
        # Test logger
        logger.info("Test log message")
        print(f"✅ Logger working")
    
        return True, settings, logger
    except Exception as e:
        print(f"❌ Config loading failed: {e}")
        traceback.print_exc()
        return False, None, None

def test_database(settings, logger):
    """Test 2: Database connectivity"""
    print("\n" + "="*50)
    print("💾 TEST 2: Database Connectivity")
    print("="*50)

    try:
        from api_service.utils.database import create_database_manager
    
        db_manager = create_database_manager()
        print(f"✅ Database manager created")
    
        # Test database stats
        stats = db_manager.get_database_stats()
        print(f"✅ Database stats retrieved:")
        for key, value in stats.items():
            print(f"   - {key}: {value}")
    
        # Test simple query
        chunks = db_manager.search_chunks(limit=5)
        print(f"✅ Sample query successful, found {len(chunks)} chunks")
    
        if chunks:
            chunk = chunks[0]
            print(f"   Sample chunk ID: {chunk.get('chunk_id', 'N/A')}")
            print(f"   Sample text: {chunk.get('text', '')[:100]}...")
    
        return True, db_manager
    except Exception as e:
        print(f"❌ Database test failed: {e}")
        traceback.print_exc()
        return False, None

def test_embeddings(settings, logger):
    """Test 3: Embeddings model"""
    print("\n" + "="*50)
    print("🧠 TEST 3: Embeddings Model")
    print("="*50)

    try:
        from api_service.models.embeddings import VietnameseEmbeddings
    
        print(f"Loading model: {settings.EMBEDDING_MODEL}")
        start_time = time.time()
    
        embeddings = VietnameseEmbeddings()
        load_time = time.time() - start_time
        print(f"✅ Embeddings model loaded in {load_time:.2f}s")
    
        # Test encoding
        test_text = "Lý Thái Tổ trị vì từ năm 1009"
        print(f"Testing text: '{test_text}'")
    
        start_time = time.time()
        vector = embeddings.encode(test_text)
        encode_time = time.time() - start_time
    
        print(f"✅ Text encoded in {encode_time:.3f}s")
        print(f"   Vector shape: {vector.shape}")
        print(f"   Vector type: {vector.dtype}")
        print(f"   Vector norm: {np.linalg.norm(vector):.6f}")
        print(f"   Sample values: {vector[:5]}")
    
        # Test batch encoding
        test_texts = [
            "Lý Thái Tổ trị vì từ năm 1009",
            "Thời gian trị vì của ông chủ yếu",
            "Lịch sử Việt Nam"
        ]
    
        start_time = time.time()
        vectors = embeddings.encode_batch(test_texts)
        batch_time = time.time() - start_time
    
        print(f"✅ Batch encoding successful in {batch_time:.3f}s")
        print(f"   Batch shape: {vectors.shape}")
    
        return True, embeddings
    except Exception as e:
        print(f"❌ Embeddings test failed: {e}")
        traceback.print_exc()
        return False, None

def test_faiss_index(settings, logger):
    """Test 4: FAISS Index"""
    print("\n" + "="*50)
    print("🔢 TEST 4: FAISS Index")
    print("="*50)

    try:
        from api_service.utils.indexing import create_faiss_manager
    
        faiss_manager = create_faiss_manager()
        print(f"✅ FAISS manager created")
    
        # Test index stats
        stats = faiss_manager.get_stats()
        print(f"✅ FAISS stats retrieved:")
        for key, value in stats.items():
            print(f"   - {key}: {value}")
    
        if stats.get('total_vectors', 0) > 0:
            # Test search with dummy query
            print(f"Testing search with {stats['total_vectors']} vectors...")
    
            # Create random query vector
            query_vector = np.random.random(settings.EMBEDDING_DIMENSION).astype(np.float32)
            query_vector = query_vector / np.linalg.norm(query_vector)  # Normalize
    
            start_time = time.time()
            distances, ids = faiss_manager.search(query_vector, top_k=5)
            search_time = time.time() - start_time
    
            print(f"✅ FAISS search completed in {search_time:.3f}s")
            print(f"   Found {len(ids[0])} results")
            print(f"   Result IDs: {ids[0]}")
            print(f"   Distances: {distances[0]}")
        else:
            print("⚠️  No vectors in FAISS index")
    
        return True, faiss_manager
    except Exception as e:
        print(f"❌ FAISS test failed: {e}")
        traceback.print_exc()
        return False, None

def test_faiss_retriever(db_manager, faiss_manager, embeddings, logger):
    """Test 5: FAISS Retriever"""
    print("\n" + "="*50)
    print("🔍 TEST 5: FAISS Retriever")
    print("="*50)

    try:
        from api_service.retrieval.faiss_retriever import FAISSRetriever
    
        faiss_retriever = FAISSRetriever()
        print(f"✅ FAISS retriever created")
    
        # Test search
        query = "Lý Thái Tổ trị vì"
        print(f"Testing query: '{query}'")
    
        start_time = time.time()
        results = faiss_retriever.search(query, top_k=3)
        search_time = time.time() - start_time
    
        print(f"✅ FAISS retriever search completed in {search_time:.3f}s")
        print(f"   Found {len(results)} results")
    
        for i, result in enumerate(results[:2]):
            print(f"   Result {i+1}:")
            print(f"     - Chunk ID: {result.get('chunk_id', 'N/A')}")
            print(f"     - Score: {result.get('score', 'N/A')}")
            print(f"     - Text: {result.get('text', '')[:100]}...")
    
        return True, faiss_retriever
    except Exception as e:
        print(f"❌ FAISS retriever test failed: {e}")
        traceback.print_exc()
        return False, None

def test_bm25_retriever(db_manager, logger):
    """Test 6: BM25 Retriever"""
    print("\n" + "="*50)
    print("📝 TEST 6: BM25 Retriever")
    print("="*50)

    try:
        from api_service.retrieval.bm25_retriever import BM25Retriever
    
        bm25_retriever = BM25Retriever()
        print(f"✅ BM25 retriever created")
    
        # Test search
        query = "Lý Thái Tổ trị vì"
        print(f"Testing query: '{query}'")
    
        start_time = time.time()
        results = bm25_retriever.search(query, top_k=3)
        search_time = time.time() - start_time
    
        print(f"✅ BM25 retriever search completed in {search_time:.3f}s")
        print(f"   Found {len(results)} results")
    
        for i, result in enumerate(results[:2]):
            print(f"   Result {i+1}:")
            print(f"     - Chunk ID: {result.get('chunk_id', 'N/A')}")
            print(f"     - Score: {result.get('score', 'N/A')}")
            print(f"     - Text: {result.get('text', '')[:100]}...")
    
        return True, bm25_retriever
    except Exception as e:
        print(f"❌ BM25 retriever test failed: {e}")
        traceback.print_exc()
        return False, None

def test_hybrid_retriever(logger):
    """Test 7: Hybrid Retriever"""
    print("\n" + "="*50)
    print("🔄 TEST 7: Hybrid Retriever")
    print("="*50)

    try:
        from api_service.retrieval.hybrid_retriever import HybridRetriever
    
        hybrid_retriever = HybridRetriever()
        print(f"✅ Hybrid retriever created")
    
        # Test search
        query = "Lý Thái Tổ trị vì"
        print(f"Testing query: '{query}'")
    
        start_time = time.time()
        results = hybrid_retriever.search(
            query=query,
            top_k=5,
            faiss_weight=0.7,
            bm25_weight=0.3
        )
        search_time = time.time() - start_time
    
        print(f"✅ Hybrid retriever search completed in {search_time:.3f}s")
        print(f"   Found {len(results)} results")
    
        for i, result in enumerate(results[:3]):
            print(f"   Result {i+1}:")
            print(f"     - Chunk ID: {result.get('chunk_id', 'N/A')}")
            print(f"     - Final Score: {result.get('final_score', 'N/A')}")
            print(f"     - FAISS Score: {result.get('faiss_score', 'N/A')}")
            print(f"     - BM25 Score: {result.get('bm25_score', 'N/A')}")
            print(f"     - Text: {result.get('text', '')[:100]}...")
    
        return True, hybrid_retriever
    except Exception as e:
        print(f"❌ Hybrid retriever test failed: {e}")
        traceback.print_exc()
        return False, None

def test_fastapi_direct():
    """Test 8: FastAPI App Direct Call"""
    print("\n" + "="*50)
    print("🌐 TEST 8: FastAPI App Direct Call")
    print("="*50)

    try:
        from api_service.main import app
        from fastapi.testclient import TestClient
    
        client = TestClient(app)
        print(f"✅ FastAPI test client created")
    
        # Test health endpoint
        response = client.get("/health")
        print(f"✅ Health endpoint: {response.status_code}")
        print(f"   Response: {response.json()}")
    
        # Test search endpoint
        search_request = {
            "query": "Lý Thái Tổ trị vì",
            "top_k": 3
        }
    
        start_time = time.time()
        response = client.post("/search", json=search_request)
        search_time = time.time() - start_time
    
        print(f"✅ Search endpoint: {response.status_code} in {search_time:.3f}s")
    
        if response.status_code == 200:
            data = response.json()
            print(f"   Found {len(data.get('results', []))} results")
            print(f"   Query time: {data.get('query_time', 'N/A')}s")
    
            for i, result in enumerate(data.get('results', [])[:2]):
                print(f"   Result {i+1}: {result.get('chunk_id', 'N/A')}")
        else:
            print(f"   Error: {response.text}")
    
        return response.status_code == 200
    except Exception as e:
        print(f"❌ FastAPI direct test failed: {e}")
        traceback.print_exc()
        return False

def test_api_server():
    """Test 9: API Server via HTTP"""
    print("\n" + "="*50)
    print("🚀 TEST 9: API Server via HTTP")
    print("="*50)

    try:
        import requests
        from config import settings
    
        base_url = f"http://127.0.0.1:{settings.API_PORT}"
        print(f"Testing API at: {base_url}")
    
        # Test health
        try:
            response = requests.get(f"{base_url}/health", timeout=10)
            print(f"✅ Health check: {response.status_code}")
            print(f"   Response: {response.json()}")
        except requests.exceptions.ConnectionError:
            print("❌ Cannot connect to API server")
            print("   Make sure the server is running: python run.py")
            return False
        except Exception as e:
            print(f"❌ Health check failed: {e}")
            return False
    
        # Test search
        search_request = {
            "query": "Lý Thái Tổ trị vì",
            "top_k": 3
        }
    
        start_time = time.time()
        response = requests.post(f"{base_url}/search", json=search_request, timeout=30)
        search_time = time.time() - start_time
    
        print(f"✅ Search request: {response.status_code} in {search_time:.3f}s")
    
        if response.status_code == 200:
            data = response.json()
            print(f"   Found {len(data.get('results', []))} results")
    
            for i, result in enumerate(data.get('results', [])[:2]):
                print(f"   Result {i+1}: {result.get('chunk_id', 'N/A')}")
                print(f"     Score: {result.get('final_score', 'N/A')}")
        else:
            print(f"   Error: {response.text}")
    
        return response.status_code == 200
    except Exception as e:
        print(f"❌ API server test failed: {e}")
        traceback.print_exc()
        return False

def main():
    """Run all debug tests"""
    print("🐛 RAG System Component Debug")
    print("Testing each component individually...")

    results = {}
    
    # Test 1: Config
    success, settings, logger = test_config()
    results['config'] = success
    if not success:
        print("\n❌ Config test failed. Cannot continue.")
        return
    
    # Test 2: Database
    success, db_manager = test_database(settings, logger)
    results['database'] = success
    if not success:
        print("\n⚠️  Database test failed. Some tests may not work.")
        db_manager = None
    
    # Test 3: Embeddings
    success, embeddings = test_embeddings(settings, logger)
    results['embeddings'] = success
    print("\n" + "="*50)
    print("🧠 TEST 3: Embeddings Model")
    print("="*50)
    print(f"Loading model: {settings.EMBEDDING_MODEL}")
    start_time = time.time()
    load_time = time.time() - start_time
    print(f"✅ Embeddings model loaded in {load_time:.2f}s")
    # Test encoding
    test_text = "Lý Thái Tổ trị vì từ năm 1009"
    print(f"Testing text: '{test_text}'")
    start_time = time.time()
    vector = embeddings.encode(test_text)
    encode_time = time.time() - start_time
    
    print(f"✅ Text encoded in {encode_time:.3f}s")
    print(f"   Vector shape: {vector.shape}")
    print(f"   Vector type: {vector.dtype}")
    print(f"   Vector norm: {np.linalg.norm(vector):.6f}")
    print(f"   Sample values: {vector[:5]}")
    
    # Test batch encoding
    test_texts = [
        "Lý Thái Tổ trị vì từ năm 1009",
        "Thời gian trị vì của ông chủ yếu",
        "Lịch sử Việt Nam"
    ]
    
    start_time = time.time()
    vectors = embeddings.encode_batch(test_texts)
    batch_time = time.time() - start_time
    
    print(f"✅ Batch encoding successful in {batch_time:.3f}s")
    print(f"   Batch shape: {vectors.shape}")
    
    if not success:
        print("\n⚠️  Embeddings test failed. FAISS tests may not work.")
        embeddings = None
    
    # Test 4: FAISS Index
    success, faiss_manager = test_faiss_index(settings, logger)
    results['faiss_index'] = success
    if not success:
        print("\n⚠️  FAISS index test failed. Search tests may not work.")
        faiss_manager = None
    
    # Test 5: FAISS Retriever
    if db_manager and faiss_manager and embeddings:
        success, faiss_retriever = test_faiss_retriever(db_manager, faiss_manager, embeddings, logger)
        results['faiss_retriever'] = success
    else:
        print("\n⚠️  Skipping FAISS retriever test due to dependencies")
        results['faiss_retriever'] = False
    
    # Test 6: BM25 Retriever
    if db_manager:
        success, bm25_retriever = test_bm25_retriever(db_manager, logger)
        results['bm25_retriever'] = success
    else:
        print("\n⚠️  Skipping BM25 retriever test due to dependencies")
        results['bm25_retriever'] = False
    
    # Test 7: Hybrid Retriever
    success, hybrid_retriever = test_hybrid_retriever(logger)
    results['hybrid_retriever'] = success
    
    # Test 8: FastAPI Direct
    success = test_fastapi_direct()
    results['fastapi_direct'] = success
    
    # Test 9: API Server
    success = test_api_server()
    results['api_server'] = success
    
    # Summary
    print("\n" + "="*60)
    print("📊 DEBUG SUMMARY")
    print("="*60)
    
    for test_name, passed in results.items():
        status = "✅ PASS" if passed else "❌ FAIL"
        print(f"{status} {test_name}")
    
    total_tests = len(results)
    passed_tests = sum(results.values())
    
    print(f"\nResult: {passed_tests}/{total_tests} tests passed")
    
    if passed_tests == total_tests:
        print("🎉 All tests passed! System is working correctly.")
    else:
        print("🚨 Some tests failed. Check the error messages above.")
    
        # Provide specific guidance
        if not results.get('database'):
            print("\n💡 Database issues:")
            print("   - Run: python scripts/init_system.py")
            print("   - Check DATABASE_PATH in config")
    
        if not results.get('faiss_index'):
            print("\n💡 FAISS index issues:")
            print("   - Run: python scripts/import_data.py")
            print("   - Check if you have data in ingested_json folder")
    
        if not results.get('api_server'):
            print("\n💡 API server issues:")
            print("   - Start server: python run.py")
            print("   - Check if port 8000 is available")

if __name__ == "__main__":
    main()
end of lasttest.py

----------------------------------------------------------------------------------------------

LOG 1, at same time
PS D:\Projects\undertest\docsearch> python.exe .\lasttest.py
🐛 RAG System Component Debug
Testing each component individually...

==================================================
🔧 TEST 1: Config Loading
==================================================
2025-08-18 06:52:27,201 - config.settings - INFO - <module>:81 - Cấu hình đã được tải. Chạy trên thiết bị: cuda
✅ Config loaded successfully

- DATABASE_PATH: D:\Projects\undertest\docsearch\data\metadata.db
- FAISS_INDEX_PATH: D:\Projects\undertest\docsearch\data\indexes\index.faiss
- EMBEDDING_MODEL: AITeamVN/Vietnamese_Embedding
- EMBEDDING_DEVICE: cuda
- EMBEDDING_DIMENSION: 1024
  2025-08-18 06:52:27,202 - config.settings - INFO - test_config:34 - Test log message
  ✅ Logger working

==================================================
💾 TEST 2: Database Connectivity
==================================================
2025-08-18 06:52:27,208 - api_service.utils.database - INFO - _initialize_database:90 - Database schema and settings initialized successfully.
2025-08-18 06:52:27,208 - api_service.utils.database - INFO - __init__:60 - DatabaseManager initialized successfully for database at: D:\Projects\undertest\docsearch\data\metadata.db
2025-08-18 06:52:27,208 - api_service.utils.database - INFO - create_database_manager:762 - Database Manager created successfully
✅ Database manager created
✅ Database stats retrieved:

- total_chunks: 120
- active_chunks: 120
- inactive_chunks: 0
- chunks_with_embeddings: 120
- total_documents: 5
- database_size_mb: 5.67578125
- recent_updates_7d: 120
  ✅ Sample query successful, found 5 chunks
  Sample chunk ID: vinacap-008
  Sample text:  2026 , mở ra cơ_hội lớn cho cả nhà đầu_tư trong và ngoài nước ....

==================================================
🧠 TEST 3: Embeddings Model
==================================================
Loading model: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:30,621 - api_service.models.embeddings - INFO - _load_model:80 - Loading model AITeamVN/Vietnamese_Embedding...
2025-08-18 06:52:36,077 - api_service.models.embeddings - INFO - _load_model:105 - Model loaded successfully in 5.45s
2025-08-18 06:52:36,077 - api_service.models.embeddings - INFO - _load_model:106 - Actual embedding dimension: 1024
2025-08-18 06:52:36,078 - api_service.models.embeddings - INFO - __init__:73 - Vietnamese Embedding Model initialized on cuda
2025-08-18 06:52:36,078 - api_service.models.embeddings - INFO - __init__:74 - Model: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:36,079 - api_service.models.embeddings - INFO - __init__:75 - Embedding dimension: 1024
✅ Embeddings model loaded in 5.46s
Testing text: 'Lý Thái Tổ trị vì từ năm 1009'
✅ Text encoded in 0.030s
   Vector shape: (1024,)
   Vector type: float32
   Vector norm: 1.000000
   Sample values: [ 7.7857478e-03  5.5430166e-02  9.3258248e-05 -2.6196954e-03
 -2.1227051e-02]
✅ Batch encoding successful in 0.028s
   Batch shape: (3, 1024)

==================================================
🧠 TEST 3: Embeddings Model
==================================================
Loading model: AITeamVN/Vietnamese_Embedding
✅ Embeddings model loaded in 0.00s
Testing text: 'Lý Thái Tổ trị vì từ năm 1009'
✅ Text encoded in 0.021s
   Vector shape: (1024,)
   Vector type: float32
   Vector norm: 1.000000
   Sample values: [ 7.7857478e-03  5.5430166e-02  9.3258248e-05 -2.6196954e-03
 -2.1227051e-02]
✅ Batch encoding successful in 0.023s
   Batch shape: (3, 1024)

==================================================
🔢 TEST 4: FAISS Index
==================================================
2025-08-18 06:52:36,193 - faiss.loader - INFO - <module>:131 - Loading faiss with AVX2 support.
2025-08-18 06:52:36,216 - faiss.loader - INFO - <module>:133 - Successfully loaded faiss with AVX2 support.
2025-08-18 06:52:36,222 - api_service.utils.indexing - INFO - _load_index:113 - Loaded FAISS index to CPU from D:\Projects\undertest\docsearch\data\indexes\index.faiss
2025-08-18 06:52:36,222 - api_service.utils.indexing - INFO - _load_index:115 - Index loaded with 120 vectors
2025-08-18 06:52:36,223 - api_service.utils.indexing - INFO - create_faiss_manager:420 - FAISS Index Manager created successfully
✅ FAISS manager created
✅ FAISS stats retrieved:

- total_vectors: 120
- embedding_dimension: 1024
- index_type: IndexIDMap2(IndexFlatIP)
- device: CPU
- index_file_exists: True
- index_file_size_mb: 0.46975135803222656
  Testing search with 120 vectors...
  ✅ FAISS search completed in 0.004s
  Found 5 results
  Result IDs: [46 60 58 63 47]
  Distances: [ 0.00281977  0.0018611  -0.00128274 -0.00240389 -0.00284696]

==================================================
🔍 TEST 5: FAISS Retriever
==================================================
2025-08-18 06:52:36,246 - api_service.retrieval.faiss_retriever - INFO - _initialize_model:105 - Loading embedding model: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:41,211 - api_service.retrieval.faiss_retriever - INFO - _initialize_model:110 - Embedding model moved to CUDA
2025-08-18 06:52:41,212 - api_service.utils.indexing - INFO - _load_index:113 - Loaded FAISS index to CPU from D:\Projects\undertest\docsearch\data\indexes\index.faiss
2025-08-18 06:52:41,212 - api_service.utils.indexing - INFO - _load_index:115 - Index loaded with 120 vectors
2025-08-18 06:52:41,213 - api_service.retrieval.faiss_retriever - INFO - _initialize_index_manager:126 - FAISS Index Manager initialized successfully
2025-08-18 06:52:41,213 - api_service.retrieval.faiss_retriever - INFO - __init__:99 - FAISS Retriever initialized with model: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:41,214 - api_service.retrieval.faiss_retriever - INFO - __init__:100 - Device: cuda, Index path: D:\Projects\undertest\docsearch\data\indexes\index.faiss
✅ FAISS retriever created
Testing query: 'Lý Thái Tổ trị vì'
✅ FAISS retriever search completed in 0.030s
   Found 2 results
   Result 1:
❌ FAISS retriever test failed: 'list' object has no attribute 'get'
Traceback (most recent call last):
  File "D:\Projects\undertest\docsearch\lasttest.py", line 194, in test_faiss_retriever
    print(f"     - Chunk ID: {result.get('chunk_id', 'N/A')}")
                              ^^^^^^^^^^
AttributeError: 'list' object has no attribute 'get'

==================================================
📝 TEST 6: BM25 Retriever
==================================================
2025-08-18 06:52:41,250 - api_service.retrieval.bm25_retriever - INFO - _load_index:556 - No existing BM25 index found, will create new one
✅ BM25 retriever created
Testing query: 'Lý Thái Tổ trị vì'
2025-08-18 06:52:41,251 - api_service.retrieval.bm25_retriever - WARNING - _calculate_bm25_scores:305 - No documents in index or invalid statistics
✅ BM25 retriever search completed in 0.000s
   Found 0 results

==================================================
🔄 TEST 7: Hybrid Retriever
==================================================
2025-08-18 06:52:41,254 - api_service.utils.indexing - INFO - _load_index:113 - Loaded FAISS index to CPU from D:\Projects\undertest\docsearch\data\indexes\index.faiss
2025-08-18 06:52:41,255 - api_service.utils.indexing - INFO - _load_index:115 - Index loaded with 120 vectors
2025-08-18 06:52:41,256 - api_service.utils.indexing - INFO - create_faiss_manager:420 - FAISS Index Manager created successfully
2025-08-18 06:52:41,257 - api_service.utils.database - INFO - _initialize_database:90 - Database schema and settings initialized successfully.
2025-08-18 06:52:41,268 - api_service.utils.database - INFO - __init__:60 - DatabaseManager initialized successfully for database at: D:\Projects\undertest\docsearch\data\metadata.db
2025-08-18 06:52:46,484 - api_service.retrieval.hybrid_retriever - INFO - _initialize_embedding_model:114 - Embedding model loaded: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:46,485 - api_service.retrieval.hybrid_retriever - INFO - __init__:105 - Hybrid Retriever initialized successfully
✅ Hybrid retriever created
Testing query: 'Lý Thái Tổ trị vì'
✅ Hybrid retriever search completed in 0.000s
❌ Hybrid retriever test failed: object of type 'NoneType' has no len()
Traceback (most recent call last):
  File "D:\Projects\undertest\docsearch\lasttest.py", line 265, in test_hybrid_retriever
    print(f"   Found {len(results)} results")
                      ~~~^^^^^^^^^
TypeError: object of type 'NoneType' has no len()

==================================================
🌐 TEST 8: FastAPI App Direct Call
==================================================
❌ FastAPI direct test failed: Client.__init__() got an unexpected keyword argument 'app'
Traceback (most recent call last):
  File "D:\Projects\undertest\docsearch\lasttest.py", line 291, in test_fastapi_direct
    client = TestClient(app)
  File "D:\Projects\undertest\docsearch\venvTest\Lib\site-packages\starlette\testclient.py", line 399, in __init__
    super().__init__(
    ~~~~~~~~~~~~~~~~^
        app=self.app,
        ^^^^^^^^^^^^^
    ...<4 lines>...
        cookies=cookies,
        ^^^^^^^^^^^^^^^^
    )
    ^
TypeError: Client.__init__() got an unexpected keyword argument 'app'

==================================================
🚀 TEST 9: API Server via HTTP
==================================================
Testing API at: http://127.0.0.1:8000
✅ Health check: 200
   Response: {'status': 'healthy', 'version': '1.0.0', 'components': {'faiss': {'status': 'healthy', 'total_vectors': 120}, 'database': {'status': 'healthy', 'total_chunks': 120, 'active_chunks': 120}, 'embedding_model': {'status': 'healthy', 'model_name': 'AITeamVN/Vietnamese_Embedding', 'device': 'cuda'}}, 'timestamp': 1755474766.869707}
✅ Search request: 500 in 5.830s
   Error: {"error":"object of type 'NoneType' has no len()","status_code":500,"timestamp":1755474772.6999314}

============================================================
📊 DEBUG SUMMARY
============================================================
✅ PASS config
✅ PASS database
✅ PASS embeddings
✅ PASS faiss_index
❌ FAIL faiss_retriever
✅ PASS bm25_retriever
❌ FAIL hybrid_retriever
❌ FAIL fastapi_direct
❌ FAIL api_server

Result: 5/9 tests passed
🚨 Some tests failed. Check the error messages above.

💡 API server issues:

- Start server: python run.py
- Check if port 8000 is available

LOG 2 at same time with log 1
 PS D:\Projects\undertest\docsearch> python.exe .\run.py
2025-08-18 06:52:20,275 - config.settings - INFO - <module>:81 - Cấu hình đã được tải. Chạy trên thiết bị: cuda
2025-08-18 06:52:20,275 - config.settings - INFO - main:18 - Starting RAG API Server...
2025-08-18 06:52:20,275 - config.settings - INFO - main:19 - Host: 0.0.0.0:8000        
2025-08-18 06:52:20,275 - config.settings - INFO - main:20 - Device: cuda
INFO:     Will watch for changes in these directories: ['D:\\Projects\\undertest\\docsearch']
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [5424] using WatchFiles
2025-08-18 06:52:22,554 - config.settings - INFO - <module>:81 - Cấu hình đã được tải. Chạy trên thiết bị: cuda
2025-08-18 06:52:22,560 - faiss.loader - INFO - <module>:131 - Loading faiss with AVX2 support.
2025-08-18 06:52:22,576 - faiss.loader - INFO - <module>:133 - Successfully loaded faiss with AVX2 support.
INFO:     Started server process [12520]
INFO:     Waiting for application startup.
2025-08-18 06:52:25,895 - config.settings - INFO - lifespan:87 - 🚀 Starting RAG System...
2025-08-18 06:52:25,895 - config.settings - INFO - startup_components:104 - Initializing Database Manager...
2025-08-18 06:52:25,914 - api_service.utils.database - INFO - _initialize_database:90 - Database schema and settings initialized successfully.
2025-08-18 06:52:25,915 - api_service.utils.database - INFO - __init__:60 - DatabaseManager initialized successfully for database at: D:\Projects\undertest\docsearch\data\metadata.db
2025-08-18 06:52:25,917 - api_service.utils.database - INFO - _initialize_database:90 - Database schema and settings initialized successfully.
2025-08-18 06:52:25,918 - config.settings - INFO - startup_components:109 - Loading Embedding Model...
2025-08-18 06:52:25,918 - api_service.models.embeddings - INFO - _load_model:80 - Loading model AITeamVN/Vietnamese_Embedding...
2025-08-18 06:52:31,697 - api_service.models.embeddings - INFO - _load_model:105 - Model loaded successfully in 5.78s
2025-08-18 06:52:31,697 - api_service.models.embeddings - INFO - _load_model:106 - Actual embedding dimension: 1024
2025-08-18 06:52:31,697 - api_service.models.embeddings - INFO - __init__:73 - Vietnamese Embedding Model initialized on cuda
2025-08-18 06:52:31,698 - api_service.models.embeddings - INFO - __init__:74 - Model: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:31,698 - api_service.models.embeddings - INFO - __init__:75 - Embedding dimension: 1024
2025-08-18 06:52:31,698 - api_service.models.embeddings - INFO - _load_model:80 - Loading model AITeamVN/Vietnamese_Embedding...
2025-08-18 06:52:37,200 - api_service.models.embeddings - INFO - _load_model:105 - Model loaded successfully in 5.50s
2025-08-18 06:52:37,201 - api_service.models.embeddings - INFO - _load_model:106 - Actual embedding dimension: 1024
2025-08-18 06:52:37,201 - config.settings - INFO - startup_components:114 - Initializing FAISS Index Manager...
2025-08-18 06:52:37,202 - api_service.utils.indexing - INFO - _load_index:113 - Loaded FAISS index to CPU from D:\Projects\undertest\docsearch\data\indexes\index.faiss
2025-08-18 06:52:37,202 - api_service.utils.indexing - INFO - _load_index:115 - Index loaded with 120 vectors
2025-08-18 06:52:37,202 - api_service.utils.indexing - INFO - create_faiss_manager:420 - FAISS Index Manager created successfully
2025-08-18 06:52:37,202 - config.settings - INFO - startup_components:117 - All components initialized successfully
2025-08-18 06:52:37,203 - config.settings - INFO - lifespan:89 - ✅ RAG System started successfully
INFO:     Application startup complete.
INFO:     127.0.0.1:54287 - "GET /health HTTP/1.1" 200 OK
2025-08-18 06:52:46,879 - api_service.utils.indexing - INFO - _load_index:113 - Loaded FAISS index to CPU from D:\Projects\undertest\docsearch\data\indexes\index.faiss
2025-08-18 06:52:46,879 - api_service.utils.indexing - INFO - _load_index:115 - Index loaded with 120 vectors
2025-08-18 06:52:46,879 - api_service.utils.indexing - INFO - create_faiss_manager:420 - FAISS Index Manager created successfully
2025-08-18 06:52:46,880 - api_service.utils.database - INFO - _initialize_database:90 - Database schema and settings initialized successfully.
2025-08-18 06:52:46,901 - api_service.utils.database - INFO - __init__:60 - DatabaseManager initialized successfully for database at: D:\Projects\undertest\docsearch\data\metadata.db
2025-08-18 06:52:52,698 - api_service.retrieval.hybrid_retriever - INFO - _initialize_embedding_model:114 - Embedding model loaded: AITeamVN/Vietnamese_Embedding
2025-08-18 06:52:52,699 - api_service.retrieval.hybrid_retriever - INFO - __init__:105 - Hybrid Retriever initialized successfully
2025-08-18 06:52:52,699 - config.settings - ERROR - search_documents:313 - Search failed: object of type 'NoneType' has no len()
2025-08-18 06:52:52,699 - config.settings - ERROR - http_exception_handler:466 - HTTP 500: object of type 'NoneType' has no len() - http://127.0.0.1:8000/search
INFO:     127.0.0.1:54288 - "POST /search HTTP/1.1" 500 Internal Server Error
INFO:     Shutting down
INFO:     Waiting for application shutdown.
2025-08-18 06:53:06,505 - config.settings - INFO - lifespan:94 - 🛑 Shutting down RAG System...
2025-08-18 06:53:06,506 - config.settings - INFO - shutdown_components:130 - Cleaning up FAISS Index Manager...
2025-08-18 06:53:06,507 - config.settings - INFO - shutdown_components:134 - Closing database connections...
2025-08-18 06:53:06,508 - api_service.utils.database - INFO - close:605 - DatabaseManager close method called. Connections are managed by context managers.
2025-08-18 06:53:06,509 - config.settings - INFO - shutdown_components:138 - Cleaning up Embedding Model...
2025-08-18 06:53:06,509 - config.settings - INFO - shutdown_components:141 - All components cleaned up
2025-08-18 06:53:06,509 - config.settings - INFO - lifespan:96 - ✅ RAG System shut down gracefully
INFO:     Application shutdown complete.
INFO:     Finished server process [12520]
INFO:     Stopping reloader process [5424]
2025-08-18 06:53:07,662 - config.settings - INFO - main:39 - Server stopped by user