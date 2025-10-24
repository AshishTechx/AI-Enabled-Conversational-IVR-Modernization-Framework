# IVR Middleware / API Layer Integration with ACS

##  Objective
Build a **middleware/API layer** to connect **legacy IVRs (VXML-based)** with the **Azure Communication Services (ACS) Conversational AI stack**.  
This integration enables real-time, intelligent voice interactions while maintaining the functionality of legacy IVR systems.

---

##  Project Overview
Legacy IVR systems use **VoiceXML (VXML)** for call control and interaction.  
Modern AI-driven services like **ACS** require RESTful or event-driven communication.

This middleware serves as a **bridge**, handling:
- VXML ↔ ACS message translation
- Real-time event routing
- Session management
- AI-generated responses delivered back to the IVR

---

##  Key Tasks

### 1. Design and Implement Connectors / APIs
- Develop **connectors or APIs** to enable communication between:
  - **VXML-based IVR systems** (e.g., Cisco CVP, Avaya Experience Portal)
  - **Azure Communication Services (ACS)**
- Define standard **JSON/XML schemas** for AI requests and responses
- Support:
  - REST endpoints for synchronous calls
  - WebSockets or event-based async communication
- Implement:
  - Session initiation and management  
  - Request routing  
  - AI response handling  
  - Error logging and recovery  

---

### 2. Real-Time Data Handling and System Compatibility
- Ensure **low-latency, real-time data handling**
- Translate between **VXML events** and **ACS API messages**
- Handle:
  - Speech-to-text (STT) for IVR input
  - Text-to-speech (TTS) for AI output
- Implement:
  - Retry, timeout, and failover mechanisms  
  - Context preservation across sessions  
  - Compatibility with ACS Conversation APIs  

---

### 3. Validate Integration Layer with Sample Transactions and Flow Testing
- Develop **sample IVR call flows** to validate end-to-end communication:
  - User input (DTMF/voice) → Middleware → ACS AI → IVR response
- Perform:
  - Transactional testing  
  - Latency and performance checks  
  - Error handling validation  
- Confirm:
  - Session continuity  
  - AI response accuracy  
  - Robustness of middleware  

---

##  Conceptual Architecture

| Legacy IVR System | <---> | Middleware / API | <---> | Azure Communication |
| (VXML Gateway) | XML | Integration Layer | REST | Services (ACS) |
| | | - API Router | | - Conversational AI |
| - DTMF / Voice | | - VXML ↔ JSON Translator | | - STT / TTS |
| - Prompts / Menus | | - Session Manager | | - Dialog Management |


acs-ivr-middleware/
├── src/
│ ├── connectors/
│ │ ├── vxml_connector.py
│ │ ├── acs_connector.py
│ ├── middleware/
│ │ ├── translator.py
│ │ ├── router.py
│ │ ├── session_manager.py
│ └── main.py
├── tests/
│ ├── test_integration_flow.py
│ ├── mock_acs.py
├── docs/
│ ├── architecture.md
│ ├── api_specifications.yaml
├── README.md
└── requirements.txt


## Example Flow: 

1. Caller interacts with IVR
2. Middleware receives input
3. ACS processes input
4. Middleware translates response
5. IVR delivers response to caller

## Deliverables

1. Working middleware/API layer connecting legacy IVR with ACS
2. Sample tested IVR → ACS conversational flows
3. Documentation and architecture diagrams
4. Integration testing results
