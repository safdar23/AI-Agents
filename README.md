# AutoGen Multi-Agent Conversations 

## Prerequisites

Before running this notebook, please ensure the following Dependencies are met, please follow the steps in order:
 

### Dependencies


1. **Set up Azure AI search:**
    - Create AI search service: https://learn.microsoft.com/en-us/azure/search/search-create-service-portal
    
2. **Set up Bing Search search service:**
    - Create a Bing Search Service : https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/create-bing-search-service-resource

3. **Azure AI Search, Bing Search and Azure Open AI parameters:**
    - Provide the created AI Search, Bing Search and Azure Open AI services configuration parameters in **azure.env** and **OAI_CONFIG_LIST** file 

4. Run the Notebooks
    - Install all libraries in notebooks
    - Run the **AzureAISearchsetup.ipynb** to create semantic index and to upload the provided **HotelsData_toAzureSearch.JSON** file
    - Please confirm that index is created and data is populated, there will be a success message displayed in notebook, you can check the same through Azure AI portal
    - Run the **Autogen-multi-agentchat.ipynb** to see the agent to agent communications  
5. **Autogen Tutorial and Course:**
   -  Please look at the AutoGen course at https://www.deeplearning.ai/short-courses/ai-agentic-design-patterns-with-autogen/

# Execution Sequence

1. Run the AzureAISearchsetup.ipynb to create the index and to upload the "HotelsData_toAzureSearch.JSON" along with  semantic configuration, suggester profile.

2. After the index is populated with data , run the Autogen-multi-agentchat.ipynb to craete **three AI agents (BINGsearch, COGsearch and semmarizeagnt) and related tools**.

# Agents Description

**Autogen-multi-agentchat.ipynb Notebook** demonstrates the AutoGen multi-agent communication**. The three agents defined in these notebooks are activated based on the customer intent and type of information requested. Agents switching happens on the context of the ask

**COGsearch agent** is responsible to retrieve data from enterrpise internal sources, I have used Azure AI Search, please feel free to update to connect to different enterpise data sources

**The BINGsearch agent** is activated when user asks a question which can not be addressed from enterprise datasources, in this case Agents make decision to call the BINGsearch agent

**summarizeagent** agenet takes the results from other agents, summarizes and presents to user

**Finite State Machine agent** transitions in an importanr concept covered in this notebook which allows the user to input an agent transition path to govern agent to agent transitions. This is useful and extremely important in controling and selecting most optimized agents transitions aligned to use case.

# Open Agent to Agent Communication
![plot](<Open Agent Communication-1.jpg>)






# Optimized Agent to Agent Communication



Non essnatial and non optimal agents usage also increase the risk of non essantial transitions, which leads to wastage of tokens and/or poor outcomes.



![plot](<Selective Agent Communication.jpg>)

Please look at the Description field, System prompt as this information is used by LLMs to make intelligent routing decision
