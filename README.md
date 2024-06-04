# langchain-chat-with-your-data
Contains notebooks with outputs from personal runs, saved for quick reference

## Map Reduce Retrieval Chains
Step 1, Individual LLMs, 1 per retrieved document
![Screenshot 2024-06-03 at 6 37 03 PM](https://github.com/unnitin/langchain-chat-with-your-data/assets/14156349/a70e9e2f-f2cf-4c43-bb44-93f14ebcee95)

Step 2, StuffDocument LLM, all outputs from individual LLM runs are stuffed together and passed as context to answer the question 
![Screenshot 2024-06-03 at 7 15 45 PM](https://github.com/unnitin/langchain-chat-with-your-data/assets/14156349/e0b59a33-d976-4d66-af62-35f36fd10a54)


Notes - 
1. From the LHS of the panel, we see the calls to MapReduce -> LLM Chain and StuffDocument Chain
2. Inspecting `metadata` for the first LLM Chain we see that the original question posed to LLM once for each document chunk retreived by vectorDB
3. All the output text returned by each LLM (4 in this example) are then `stuffed` together and passed into LLM for the same question again
4. Answer from the StuffDocument chain is returned


## Refine Retrieval Chains


Note - All original content belongs to DeepLearning.AI; I am only saving my specific runs of notebooks with a few examples based on understanding from the course
