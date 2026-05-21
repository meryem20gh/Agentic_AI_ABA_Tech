# Day 4: Agent Memory & Persistence Patterns

## Overview
Day 4 explores advanced agentic patterns focusing on **persistent agent memory** and **intelligent message routing**. These workflows demonstrate how AI agents can maintain context and intelligent decision-making at scale.

## 🎯 Learning Objectives
- Implement persistent memory storage for agentic systems
- Integrate databases (MongoDB) with AI workflows
- Build intelligent routing mechanisms for message handling
- Understand context retention and historical reasoning
- Master complex multi-component orchestration

## 📁 Workflows

### 1. **Agent Memory - MongoDB**
**File**: `Agenet memory - MongoDB.json`

#### Purpose
Implements an agentic memory system using MongoDB as persistent storage, enabling the AI agent to maintain conversation history and retrieve relevant context for informed decision-making.

#### Architecture Components

```
ChatInput 
    ↓
Prompt Template (with conversation history)
    ↓
[MongoDB Component] ←→ Parser Component
    ↓                        ↓
GroqModel (LLM Inference) ← Parsed Context
    ↓
Prompt Template (Response Generation)
    ↓
PythonREPL Component
    ↓
ChatOutput
```

#### Component Details

| Component | Purpose | Key Features |
|-----------|---------|--------------|
| **Chat Input** | Message entry point | Captures user messages with session tracking |
| **MongoDB Component** | Database queries | Retrieves historical messages and context |
| **Parser** | Data extraction | Formats MongoDB results into readable context |
| **Prompt Template** | Prompt engineering | Creates system prompts with conversation history |
| **GroqModel** | LLM inference | Processes prompts via Groq API |
| **PythonREPL** | Code generation & execution | Executes generated Python code dynamically |
| **Chat Output** | Result display | Returns processed responses to user |

#### Workflow Logic

1. **User Input Reception**
   - ChatInput captures user message
   - Session ID and context ID are tracked

2. **Memory Retrieval**
   - MongoDB component queries last 3 exchanges
   - Parser converts DataFrame to formatted text
   - Historical context is extracted and cleaned

3. **Context-Aware Reasoning**
   - System prompt includes conversation history
   - Current user message is analyzed with context
   - Prompt template enforces JSON output format:
     ```json
     {
       "message_user": "user's message",
       "reponse": "AI response",
       "confidence": 0.85
     }
     ```

4. **Response Generation**
   - LLM processes prompt with history
   - Second prompt template generates Python code
   - Code is executed in sandbox environment

5. **Output Delivery**
   - Results from Python execution are returned
   - Chat output displays formatted response

#### Use Cases
- **Contextual Q&A**: Maintain conversation context across sessions
- **Personalized Responses**: Reference historical interactions
- **Decision Making**: Use past patterns for informed choices
- **Multi-turn Conversations**: Build coherent dialogue flows
- **Audit Trail**: Complete conversation history in MongoDB

#### Configuration Highlights
- **Language**: French (customizable)
- **Memory Backend**: MongoDB
- **LLM Model**: Groq API
- **Output Format**: Structured JSON
- **Confidence Scoring**: 0.0-1.0 scale

#### Practical Example

```
User: "Rappelle-moi ce que j'ai demandé hier"
System: [Queries MongoDB for previous session]
Memory: "Yesterday you asked about project timelines"
LLM Response: {
  "message_user": "Rappelle-moi ce que j'ai demandé hier",
  "reponse": "Hier, vous aviez demandé des informations...",
  "confidence": 0.92
}
```

---

### 2. **Agent Memory - Message History**
**File**: `Agent memory - Message History.json`

#### Purpose
Implements intelligent message routing using category-based decision logic, enabling the agent to handle different message types with specialized processing paths.

#### Architecture Components

```
ChatInput
    ↓
SmartRouter (Category Detection)
    ├─→ Category 1 Path → GroqModel 1
    ├─→ Category 2 Path → GroqModel 2
    ├─→ Category 3 Path → GroqModel 3
    └─→ Default Path → GroqModel (Default)
    ↓
ChatOutput
```

#### Component Details

| Component | Purpose | Key Features |
|-----------|---------|--------------|
| **Chat Input** | Message entry | Accepts incoming messages |
| **Smart Router** | Intelligent routing | Categorizes and routes to appropriate handler |
| **GroqModel (Multiple)** | Category-specific processing | Specialized LLMs for each message type |
| **Chat Output** | Result display | Returns categorized response |

#### Routing Logic

The SmartRouter analyzes incoming messages and determines the best processing path:

- **Category 1**: Technical/Support issues → Technical handler
- **Category 2**: Billing/Administrative → Administrative handler
- **Category 3**: General inquiries → General handler
- **Default**: Unknown/Miscellaneous → Default handler

#### Workflow Logic

1. **Message Reception**
   - User message enters via ChatInput
   - Session context is established

2. **Intelligent Categorization**
   - SmartRouter analyzes message content
   - Determines appropriate category
   - Routes to specialized handler

3. **Category-Specific Processing**
   - Each category has optimized LLM configuration
   - Specialized prompting strategy
   - Tailored response format

4. **Response Generation & Delivery**
   - GroqModel processes via appropriate prompt
   - ChatOutput returns formatted response

#### Use Cases
- **Multi-department Routing**: Route to appropriate team handler
- **Intent Classification**: Automatically categorize user intent
- **Specialized Responses**: Different response strategies per category
- **Load Distribution**: Distribute work across specialized agents
- **Triage Systems**: Healthcare/support ticket prioritization

#### Example Routing

```
Input: "My account won't login and I'm getting error 401"
Router Analysis: Technical issue detected
Route: Category 1 (Technical)
Handler: Tech-specialized GroqModel
Response: Troubleshooting steps with technical details

Input: "What's my current bill amount?"
Router Analysis: Billing question detected
Route: Category 2 (Administrative)
Handler: Admin-specialized GroqModel
Response: Account summary with billing information
```

---

## 🔄 Comparison: MongoDB vs. Message History

| Feature | MongoDB Workflow | Message History Workflow |
|---------|------------------|--------------------------|
| **Memory Type** | Persistent database | Current session routing |
| **Storage** | MongoDB collection | Router state |
| **Use Case** | Long-term context | Real-time categorization |
| **Complexity** | Complex multi-step | Streamlined routing |
| **Scaling** | Database-backed | In-memory routing |
| **History** | Complete audit trail | Active session only |

---

## 🚀 Implementation Guidelines

### MongoDB Workflow Setup
```json
{
  "database_config": {
    "uri": "mongodb://localhost:27017",
    "database": "agent_memory",
    "collection": "conversations"
  },
  "query_params": {
    "limit": 3,
    "sort": {"timestamp": -1}
  }
}
```

### Message Router Setup
```json
{
  "categories": [
    {"name": "technical", "keywords": ["error", "bug", "not working"]},
    {"name": "billing", "keywords": ["bill", "charge", "invoice"]},
    {"name": "general", "keywords": ["question", "info", "help"]}
  ],
  "default_category": "general"
}
```

---

## 💡 Key Patterns & Techniques

### Pattern 1: History Context Injection
```
Template: "Previous exchanges: {history}\n\nCurrent message: {user_message}"
```
This ensures the LLM considers historical context before responding.

### Pattern 2: Confidence Scoring
```json
{
  "confidence": 0.85,
  "reason": "Based on 3 previous similar exchanges"
}
```
Quantify LLM certainty for response validation.

### Pattern 3: Dynamic Routing
```
IF message.contains("technical_keyword") THEN route_to_technical
ELSE IF message.contains("billing_keyword") THEN route_to_billing
ELSE route_to_default
```

### Pattern 4: Structured Output
```json
{
  "message_user": "original message",
  "reponse": "generated response",
  "confidence": 0.0-1.0,
  "category": "detected category",
  "reasoning": "why this response"
}
```

---

## 🔧 Technical Stack

- **Persistence Layer**: MongoDB
- **LLM Provider**: Groq API
- **Routing Engine**: Smart Router Component
- **Data Processing**: Parser Component
- **Code Execution**: Python REPL Component
- **Platform**: LangFlow

---

## 🎓 Advanced Topics Covered

1. **Stateful Agent Architecture**: Maintaining context across requests
2. **Database Integration**: Seamless MongoDB connectivity
3. **Dynamic Routing**: Intelligent message categorization
4. **Confidence Metrics**: Quantifying AI decision certainty
5. **Code Generation**: LLM-generated and executed Python
6. **Multi-path Orchestration**: Parallel processing with convergence
7. **Session Management**: Context and session ID tracking
8. **Data Transformation**: Complex parsing and formatting

---

## 📊 Performance Considerations

### MongoDB Workflow
- **Query Speed**: Index historical messages by session_id
- **Memory**: Use pagination for large history (limit: 3)
- **Scalability**: Database-backed for unlimited history

### Message Router Workflow
- **Latency**: Low-latency routing (in-memory)
- **Throughput**: High throughput for parallel paths
- **Accuracy**: Rule-based routing (highly reliable)

---

## 🔗 Integration Points

- **Session Management**: Persistent session IDs for context
- **Message Storage**: MongoDB collections for history
- **LLM APIs**: Groq integration for inference
- **Code Execution**: Sandboxed Python environment
- **User Interface**: Chat output for user interaction

---

## 📝 Next Steps

1. **Day 5**: Introduce multi-agent coordination and collaboration
2. **Day 6**: Implement feedback loops and learning mechanisms
3. **Day 7**: Scale to production with monitoring and optimization

---

## 📚 Resources

- [MongoDB Documentation](https://docs.mongodb.com/)
- [Groq API Guide](https://groq.com/docs)
- [LangFlow Components](https://docs.langflow.org)
- [Agent Architecture Best Practices](https://docs.anthropic.com/claude/reference/agents)

---

## ✨ Key Takeaways

- **Persistence**: MongoDB enables long-term agent memory
- **Context**: Historical context improves decision quality
- **Routing**: Smart routing optimizes message handling
- **Confidence**: Scoring adds transparency to agent decisions
- **Scalability**: Database-backed systems scale effortlessly
