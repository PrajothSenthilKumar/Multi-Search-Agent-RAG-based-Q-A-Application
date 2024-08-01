# Multi-Search-Agent-RAG-based-Q-A-Application-using-open-source-models

**As a first step, create a virtual environment using the command "conda create -p venv python==3.12" and activate the environment "conda activate '.....\venv'". Then install the necessary modules by "pip install -r requirements.txt".**

**Note: Use your virtual environment python interpreter as your kernel.**

**We will be using three tools,**

**1) Create a wrapper on top of Wikipedia to interact with the Wikipedia tool. For Wikipedia, we don't need to create a separate API Wrapper since the Langchain is already taking care of it.**

![Wikipedia_SS](https://github.com/user-attachments/assets/f2c7e576-c50d-4a52-85ac-deb6160b7a7c)


**2) Before using OpenAI models, we must create and download the openai_api_key from "https://platform.openai.com/api-keys". Then store the key as a variable in your system environment variables like "OPENAI_API_KEY": "......".**
   

![OpenAI_API_KeySS](https://github.com/user-attachments/assets/03b79013-f3b4-4227-9bfd-a2fd51731bf8)


**To load the environment variable into our environment, using**


![Loading_variableSS](https://github.com/user-attachments/assets/3cb06a8a-64b4-4546-bf9d-f82ec48c87f0)


**4) Next we will create the second tool by reading the contents of a particular website as data sources. This is a custom tool. We would load the documents using "document_loaders" and split them into chunks using "RecursiveCharacterTextSplitter".**

**With the OpenAIEmbeddings from OpenAI, we would create embeddings of the chunks and store them in vectorDB FAISS. Make this DB a retriever.**


![Customtool1_SS](https://github.com/user-attachments/assets/3a95b0b9-cb5f-4bdb-b964-705032df9551)

![Customtool2_SS](https://github.com/user-attachments/assets/d850a342-02f3-4c24-8044-e68a741d04a7)



**5) In the previous step, we created a retriever. With the help of the retriever, we would create a tool to search and retrieve documents with the help of "create_retriever_tool".**


![Create_retriever_toolSS](https://github.com/user-attachments/assets/65d70816-9e91-4b50-b767-c67f69534323)



**6) Thirdly, again we will create a wrapper on top of Arxiv to interact with the Arxiv webpage. Similar to Wikipedia, for Arxiv tool Langchain provides APIWrapper.**
   

![ArxivToolSS](https://github.com/user-attachments/assets/d28e8435-d300-4f0e-88ef-94e33907b9a4)


**7) Finally, combine all the tools created (wiki, Arxiv, retriever_tool) into a list "tools".**


![AllToolsSS](https://github.com/user-attachments/assets/832ff293-db99-4bf5-a2d5-21a50abcad0b)


**8) Create and initialize the LLM from OpenAI models using the "langchain_openai" module.**


![LLM_SS](https://github.com/user-attachments/assets/6452ec4c-c72a-4887-a9b9-1d3d01157d86)


**9) Now create the prompt from predefined prompt templates in the "Hub" package from Langchain --> "hwchase17/openai-functions-agent"**


![PromptHubSS](https://github.com/user-attachments/assets/441b4860-83d4-450b-befd-a63865d69f9a)

![PromptHubSS1](https://github.com/user-attachments/assets/d24382d5-f2dc-43c9-9cfa-f7af755aeece)


**10) Atlast initialize the agent "create_openai_tools_agent" from "langchain.agents" module with the LLM, tools, and the Prompt.**


![AgentSS](https://github.com/user-attachments/assets/8955da37-2747-4bae-be63-7a62521dfff2)


**11) Create an object for the AgentExecutor class to invoke the created agent.**


![AgentExecutorSS](https://github.com/user-attachments/assets/815bae6f-6c2f-4305-bdf8-85788a3c9a0c)


**12) Finally, invoke the agent with an input to generate a response from all three tools.**


![Output_1](https://github.com/user-attachments/assets/08812678-ce01-45d4-b47c-fbf4f22b04ba)

![Output_2](https://github.com/user-attachments/assets/49d09f8d-6c7b-4526-ab62-58ceb84219dc)

![Output_3](https://github.com/user-attachments/assets/191c1735-7945-478a-b036-1a8abae89eec)

![Output_4](https://github.com/user-attachments/assets/a01409db-476f-45cd-8c6b-f3b90f5da453)

![Output_5](https://github.com/user-attachments/assets/804307e8-6414-48cb-86c7-c6b732bfc18b)

![Output_6](https://github.com/user-attachments/assets/480d2f9d-69bb-4a41-826a-bf954a345148)

**"Finally we got the required answer from the data provided by the tools."**

**Note:- Don't forget to add your openai_api_key in the system environment variables.**













 










