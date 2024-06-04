# langchain-chat-with-your-data
Contains notebooks with outputs from personal runs from the [langchain-course](https://www.coursera.org/learn/langchain-chat-with-your-data-project/home/week/1), saved for quick reference

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
Relatively simpler construction, original question is passed in sequence with retrieved documents
For each LLM call, we pass output from any the previous LLM alongwith the retrieved document as context, we ask LLM to refine answer if needed
* Note existing answer, context str and output in the attached picture
![Screenshot 2024-06-03 at 6 36 47 PM](https://github.com/unnitin/langchain-chat-with-your-data/assets/14156349/4f08886e-ebbe-47ff-bb5a-ab43dbf25d0a)

## Adding memory to chat
Step 1, Memory is used to store previous messages in the chat, prompt asks LLM to use the conversation to re-phrase the follow up question to function as a stand-alone question
![Screenshot 2024-06-04 at 11 18 42 AM](https://github.com/unnitin/langchain-chat-with-your-data/assets/14156349/e57d13de-8375-431f-bae8-61e2c08a2d9f)

Step 2, LLM is passed all the extracted documents and chat history to answer the re-phrased, standalone question from `Step 1`
![Screenshot 2024-06-04 at 11 19 53 AM](https://github.com/unnitin/langchain-chat-with-your-data/assets/14156349/37ed79d7-5369-4828-905b-49fbae6b2d4d)


Note - All original content belongs to DeepLearning.AI; I am only saving my specific runs of notebooks with a few examples based on understanding from the course
