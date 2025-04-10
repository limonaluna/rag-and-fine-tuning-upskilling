# RAG and Fine-Tuning Upskilling Workshop
This repository is designed to support hands-on learning and upskilling in **Retrieval-Augmented Generation (RAG)** and **Fine-Tuning of Large Language Models (LLMs)** with Azure OpenAI and Azure AI Search. It includes detailed setup instructions, practical notebooks and guided experiences to help you build, customize, and optimize GenAI applications using Microsoft Azure.

## 📚 What’s Inside
This upskilling repo is **based on and extends** the following Microsoft resources:

* [RAG Time](https://github.com/microsoft/rag-time) by Microsoft
* [LLM-Fine-Tuning-Azure](https://github.com/microsoft/LLM-Fine-Tuning-Azure/tree/main) by Microsoft.

The content has been adapted and enriched to provide a smoother and more guided learning experience, ideal for workshops or self-paced exploration.

## 📁 Repository Structure

### **01 – Azure Resource Setup**  
🧱 **Foundation for Everything**  
Before doing anything else, you’ll need to set up the essential Azure services: **Azure OpenAI**, **Azure AI Search**, and **Azure Storage**.  
This step lays the groundwork for all following steps.

> 🔧 **To Do:** Manual, no-code setup using the Azure Portal.

---

### **02 – Azure AI Search Quickstart**  
🔍 **Index Setup with Vectorization**  
Use the **Import and vectorize data** wizard in the Azure Portal to create an AI Search index.  
This wizard chunks your content and uses an embedding model to vectorize it — both during indexing and querying.

> ✅ **Required for:** Step 04 and Step 05  
> 🔧 **To Do:** Manual, no-code setup using the Azure Portal.

---

### **03 – Code Environment Setup**  
💻 **Prepare Your Code Environment**  
Set up your Python environment to run the code-based exercises. You can do this locally, in a virtual environment, or using GitHub Codespaces.

> ✅ **Required for:** Step 04 and Step 05  
> 🔧 **To Do:** Choose your preferred setup (local, virtual env, or Codespaces).

---

### **04 – RAG Fundamentals**  
🤖 **Hands-On with Retrieval-Augmented Generation (RAG)**  
This notebook demonstrates how to use **Azure OpenAI** and **Azure AI Search** together to retrieve relevant documents and generate answers using a RAG approach.

> ✅ **Prerequisites:** Steps 01, 02, and 03  
> 🧪 **To Do:** Follow the notebook and complete the built-in challenges (code-first experience).

---

### **05 – Optimizing Retrieval**  
🚀 **Take Retrieval to the Next Level**  
This notebook builds on RAG Fundamentals and explores **different search strategies**: keyword, vector, hybrid, semantic ranking, and query rewriting.

> ✅ **Prerequisites:** Steps 01, 02, and 03  
> 🧪 **To Do:** Follow the notebook and complete the built-in challenges (code-first experience).

---

### **07 – LLM Fine-Tuning**  
🎯 **Fine-Tune GPT Models with Azure OpenAI**  
This is a standalone step focused on using the **Azure OpenAI Studio** to fine-tune a language model (no RAG setup required).

> ✅ **Only requires:** Step 01 (Azure setup)  
> 🔧 **To Do:** Use the Azure AI Foundry experience in the Portal (no-code).


## 🔧 Requirements
* An Azure subscription with permission to deploy resources and configure authentication:
    * Azure OpenAI
    * Azure Cognitive Search
    * Azure Storage

* Basic familiarity with Python and LLMs
* Access to Github Codespaces or possibility to run code on VS Code

## 🚀 Get Started
* To begin, follow the instructions in 01_AzureResourceSetup.md.
* Each notebook is self-contained and walks you through code, configuration, and explanations.

## 📌 Notes
* This repo is for educational and prototyping purposes and is not production-hardened.
* You may need to request access to Azure OpenAI via the Azure OpenAI portal.

## 🙌 Acknowledgments
This work builds upon:
* [RAG Time](https://github.com/microsoft/rag-time) by Microsoft
* [LLM-Fine-Tuning-Azure](https://github.com/microsoft/LLM-Fine-Tuning-Azure/tree/main) by Microsoft