
- [`.env`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env"): Contains environment variables, such as API keys.
- [`.env.example`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env.example%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env.example"): Example of the [`.env`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env") file.
- [`.python-version`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.python-version%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.python-version"): Specifies the Python version used in the project.
- [`memory.ipynb`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/memory.ipynb"): Jupyter Notebook containing the main code for the project.
- [`requirements.txt`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/requirements.txt"): Lists the dependencies required for the project.

## Setup

1. **Clone the repository:**

    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Create a virtual environment:**

    ```sh
    python -m venv .venv
    source .venv/bin/activate  # On Windows use `.venv\Scripts\activate`
    ```

3. **Install the dependencies:**

    ```sh
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**

    - Copy [`.env.example`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env.example%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env.example") to [`.env`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env"):

        ```sh
        cp .env.example .env
        ```

    - Fill in the required values in the [`.env`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2F.env%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/.env") file.

## Usage

1. **Run the Jupyter Notebook:**

    ```sh
    jupyter notebook memory.ipynb
    ```

2. **Execute the cells in [`memory.ipynb`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%5D "/Users/manuelpaiva/Desktop/langchain-memory/memory.ipynb") to see the Conversational RAG Chain in action.**

## Key Components

- **Session History Retrieval:**

    ```python
    messages = conversational_rag_chain.get_session_history("abc123").messages
    ```

- **Message Formatting:**

    ```python
    for i, message in enumerate(messages):
        if isinstance(message, HumanMessage):
            print(f"Human: {message.content}")
        elif isinstance(message, AIMessage):
            print(f"AI: {message.content}")
        print()  # Adds a blank line between each pair of messages
    ```

- **Chain Creation:**

    ```python
    history_aware_retriever = create_history_aware_retriever(llm, retriever, contextualize_q_prompt)
    question_answer_chain = create_stuff_documents_chain(llm, qa_prompt)
    rag_chain = create_retrieval_chain(history_aware_retriever, question_answer_chain)
    ```

- **Invoke Chain:**

    ```python
    conversational_rag_chain.invoke(
        {"input": "Where the people surf in the beginnings?"},
        config={
            "configurable": {"session_id": "abc123"}
        },
    )["answer"]
    ```

## Dependencies

- [`langchain`](command:_github.copilot.openSymbolFromReferences?%5B%22langchain%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A20%2C%22character%22%3A10%7D%7D%2C%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A1%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`langchain-community`](command:_github.copilot.openSymbolFromReferences?%5B%22langchain-community%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A20%2C%22character%22%3A10%7D%7D%2C%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A1%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`langchainhub`](command:_github.copilot.openSymbolFromReferences?%5B%22langchainhub%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A2%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`langchain-chroma`](command:_github.copilot.openSymbolFromReferences?%5B%22langchain-chroma%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A20%2C%22character%22%3A10%7D%7D%2C%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A1%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`beautifulsoup4`](command:_github.copilot.openSymbolFromReferences?%5B%22beautifulsoup4%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A4%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`python-dotenv`](command:_github.copilot.openSymbolFromReferences?%5B%22python-dotenv%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A258%2C%22character%22%3A16%7D%7D%2C%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A5%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")
- [`langchain-openai`](command:_github.copilot.openSymbolFromReferences?%5B%22langchain-openai%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Fmemory.ipynb%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A20%2C%22character%22%3A10%7D%7D%2C%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22external%22%3A%22file%3A%2F%2F%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22path%22%3A%22%2FUsers%2Fmanuelpaiva%2FDesktop%2Flangchain-memory%2Frequirements.txt%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A1%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition")

## License

This project is licensed under the MIT License.