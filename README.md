# Local RAG
Self-hosted RAG-system for markdown notes using the following technologies:
- Docker
- PostgreSQL (running at port `5432`)
- n8n (running at port `5678`)
- Qdrant (running at port `6333`)
- Open-WebUI (running at port `3001`)
- Ollama (running at port `11434`)

## Installation
1. [Install Docker](https://www.docker.com/get-started/)
2. Clone repo `git clone https://github.com/miikavonbell/local-rag.git`
3. Open the project folder
4. Run: `docker compose up` and wait for it to finish (could take a few minutes)

## Getting started
1. Activate the n8n workflow by first logging in to n8n dashboard at [http://localhost:5678/](http://localhost:5678/)
    - Create account / Log in (local account)
    - Toggle `Markdown RAG` -switch to activate the workflow
2. Use your favorite Markdown-editor, like VSCode and navigate to `/content` -folder and start adding markdown-notes there.
    - Every add, change, and delete event in the content folder will update the Qdrant vector database through n8n workflow.
    - You can start by simply saving the `example.md` -file once, which will add it to the Qdrant vector store
3. Use the Open WebUI at [http://localhost:3001/](http://localhost:3001/) - to talk to your files. 
    - Login with: **username**: `test@test.fi` **password**: `test`
    - Open WebUI database should be initialized with ready-to-go setup
    - Ask and example question in Open WebUI, like: 
        - *When is Mark Down's birthday?*
        - *What is the plan for Mark Down's birthday?*

## Other
- By default, this setup includes `Qqwen2.5:7b` -model for AI, which might require some good performance from your hardware. This model was tested optimal with 32GB DDR5 7200MHz, 13700k, 7900XT.
- Open WebUI seems to sometimes timeout when webhook requests take a long time to process. Use F5 to update the chat.
- For a more detailed walk-through of this system check out the post here: [Setting up a local self-hosted AI RAG system with Docker](https://apukone.com/posts/self-hosted-local-rag-system/ "Setting up a local self-hosted AI RAG system with Docker")