# Agentic AI ABA Tech - Generation AIoT Program

## Project Overview
**Agentic AI ABA Tech** is a specialized track within the Generation AIoT program focused on exploring and implementing agentic AI workflows and autonomous agent systems. This repository contains practical implementations of AI agents solving real-world problems through intelligent automation.

## 🎯 Mission
Develop and showcase advanced agentic AI solutions that demonstrate:
- Intelligent automation using AI agents
- Multi-agent coordination and orchestration
- Practical business applications (email sorting, support routing, etc.)
- Integration of LLMs with workflow systems
- Scalable and maintainable agent architectures

## 📚 Program Structure

This project is organized by day, with each day introducing new concepts and more complex agentic patterns:

### [Day 1: Automated Email Sorting](./Day%201/README.md)
Foundational workflow demonstrating basic agentic patterns:
- Email content analysis using LLMs
- Automated classification and categorization
- Simple data transformation pipelines
- **File**: `Automated_email_sorting.json`

### [Day 2: Support Ticket Router](./Day%202/README.md)
Intermediate workflow showcasing intelligent routing:
- Smart routing based on ticket content
- Multi-path decision logic
- Intent understanding and classification
- **File**: `Support N0.json`

### [Day 3: Advanced Agentic Workflows](./Day%203/README.md)
Advanced patterns and complex orchestration:
- Multi-agent coordination
- Complex data pipelines
- Real-time event processing
- Feedback loops and learning mechanisms
- **File**: `j1-version fz.json`

### [Day 4: Agent Memory & Persistence](./Day%204/README.md)
Enterprise-grade agent memory and intelligent routing:
- Persistent agent memory with MongoDB integration
- Context-aware reasoning with historical data
- Intelligent message routing and categorization
- Multi-path orchestration and specialized handlers
- Database-backed conversation management
- **Files**: 
  - `Agenet memory - MongoDB.json` (Persistent memory system)
  - `Agent memory - Message History.json` (Smart routing system)

### [Day 5: Evaluation & Task Tracker](./Day%205/README.md)
Advanced task evaluation and management system:
- Intelligent message routing with LLM-based categorization
- Task evaluation with anomaly detection
- Multi-backend persistence (MongoDB + Notion)
- Dynamic Python code execution for analysis
- Third-party integrations and API coordination
- Quality assurance and data validation
- **File**: `Eval_task_tracker.json`

### [Day 6: RAG-Powered Legal Document Assistant](./Day%206/README.md)
Retrieval-Augmented Generation workflow for legal Q&A:
- Legal document ingestion and text chunking
- Embedding generation with Google Generative AI
- Chroma DB semantic retrieval
- Prompt-driven legal assistant responses via Groq
- Strict context-only answer generation
- **File**: `j6-RAG.json`

### [Day 7: Hybrid RAG Retrieval](./Day%207/README.md)
Advanced retrieval workflow that improves document selection:
- Hybrid semantic + keyword retrieval
- Reciprocal Rank Fusion (RRF) for better context ranking
- Python-based fusion logic before answer generation
- Stronger grounding for question-answering workflows
- **File**: `j7-RAG hybrid (2).json`

### [Day 8: Structured Data Extraction](./Day%208/README.md)
Structured extraction workflow for converting raw text into validated JSON output:
- LLM-based extraction from unstructured input
- Schema-guided structured output generation
- Pydantic validation for reliable field types
- Type conversion for downstream automation
- **Files**:
  - `extraction.json`
  - `extraction pydatic.json`

### [Day 9: Security Guard & DB-Aware Threat Detection](./Day%209/README.md)
Security-first workflow focused on prompt-injection filtering and safe routing:
- Prompt-injection and jailbreak detection
- Smart routing between safe and unsafe requests
- Groq-based justification and response handling
- Database-enabled tool integration in the DB variant
- **Files**:
  - `Agent security.json`
  - `Agent security DB.json`

### [Day 10: HR Assistant](./Day%2010/README.md)
HR-focused assistant workflow for grounded employee and policy support:
- Retrieval-based answer generation using Chroma
- Prompt templating with relevant context
- Python-based processing and LLM reasoning
- Chat-based HR support experience
- **File**: `HR assistant.json`

## 🔧 Technical Stack

### Core Technologies
- **Language Models**: Groq API for LLM inference
- **Workflow Platform**: Visual workflow definition (JSON-based)
- **Data Processing**: Type conversion and parsing components
- **Routing Logic**: Smart routing and conditional logic
- **Persistence**: MongoDB for agent memory storage
- **Code Execution**: Python REPL for dynamic code generation and execution
- **Third-Party Integration**: Notion API for dashboard and task management

### Architecture Patterns
- **Component-Based Design**: Modular, reusable workflow components
- **Event-Driven**: Message-based communication between agents
- **Extensible**: Easy to add new components and patterns
- **Scalable**: Designed for enterprise-grade deployments

## 📋 Workflow Components

### Common Components Used
- **TextInput/ChatInput**: Input interface for data and messages
- **GroqModel**: LLM inference component
- **SmartRouter**: Intelligent routing logic with LLM-based categorization
- **TypeConverter**: Data type conversion and normalization
- **Parser**: Data extraction and structuring
- **MongoDBComponent**: Database queries and persistent storage
- **PythonREPL**: Dynamic Python code generation and execution
- **Message History**: Store/retrieve conversation history
- **Notion Page Creator**: Third-party integration for task management

## 🚀 Getting Started

### Prerequisites
- Access to the agentic workflow platform
- Groq API credentials (for LLM inference)
- Understanding of AI agents and workflow design

### Quick Start
1. Choose a workflow from the Day folders
2. Import the JSON file into the workflow platform
3. Configure necessary API credentials
4. Run the workflow with sample inputs
5. Observe the agentic decision-making in action

### Example Usage

#### Email Sorting (Day 1)
```
Input: "Please review my expense report for Q4"
Output: Classified as "Administrative" | Route to Finance Team
```

#### Support Routing (Day 2)
```
Input: "My account is locked and I can't reset my password"
Output: Classified as "High Priority Account Issue" | Route to Account Recovery Team
```

#### Agent Memory & Persistence (Day 4)
**MongoDB Workflow:**
```
Input: "Rappelle-moi ce que j'ai demandé hier"
Memory: [Queries MongoDB for session history]
Output: {
  "message_user": "Rappelle-moi ce que j'ai demandé hier",
  "reponse": "Hier, vous aviez posé des questions sur les délais du projet...",
  "confidence": 0.92
}
```

**Message Router Workflow:**
```
Input: "My invoice shows an incorrect amount"
Detection: Billing category identified
Route: Administrative handler
Output: Specialized response with billing information and next steps
```

## 📖 Documentation

Each day's folder contains:
- **README.md**: Overview and usage instructions
- **\*.json**: Workflow definition files
- **Component descriptions**: Detailed component configurations

## 🔄 Workflow Execution Flow

```
Input Data
    ↓
Text/Chat Input Component
    ↓
LLM Analysis (GroqModel)
    ↓
Type Conversion
    ↓
Intelligent Routing/Processing
    ↓
Output/Action
```

## 🎓 Learning Outcomes

By completing this specialization, you will understand:
- ✅ Fundamentals of agentic AI architecture
- ✅ How to design multi-component workflows
- ✅ LLM integration patterns
- ✅ Intelligent routing and decision-making
- ✅ Practical business applications of AI agents
- ✅ Scalability and production considerations
- ✅ Persistent agent memory systems with databases
- ✅ Context-aware reasoning with historical data
- ✅ Multi-path orchestration and routing strategies
- ✅ Dynamic code generation and sandboxed execution
- ✅ Third-party API integration and orchestration
- ✅ Quality assurance and anomaly detection in workflows
- ✅ Task evaluation and multi-backend persistence

## 🔮 Future Enhancements

Planned additions to the repository:
- [ ] Multi-agent collaboration patterns
- [ ] Advanced reasoning and planning workflows
- [ ] Real-time streaming agents
- [ ] Feedback learning mechanisms
- [ ] Integration examples with popular platforms
- [ ] Performance benchmarks and optimization guides
- [ ] Testing and validation frameworks

## 📝 Contributing

When adding new workflows:
1. Create appropriate day folder if needed
2. Add JSON workflow definition
3. Include README with workflow overview
4. Document all components and data flows
5. Add usage examples

## 📞 Support

For questions about:
- **Workflows**: Check the individual README files in each day's folder
- **Components**: Review the component configurations in the JSON files
- **Program**: Refer to the Generation AIoT program documentation

## 📄 License

This project is part of the Generation AIoT program.

## 🏆 Key Achievements

This repository demonstrates:
- Real-world agentic AI applications
- Production-ready workflow patterns
- Enterprise-scale automation
- Practical AI-driven decision making

---

**Last Updated**: June 2026  
**Program**: Generation AIoT - Agentic AI Specialization  
**Repository**: Agentic_AI_ABA_Tech
