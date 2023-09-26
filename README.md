# FLaNK-watsonx.ai

FLaNK Stack with watsonx.ai for google/flan-ul2, google/flan-t5-xxl, Granite and other foundation models


### Videos

https://www.youtube.com/watch?v=RPz7Xm4fLF4


### Models

* google/flan-ul2

* google/flan-t5-xxl

* granite-13b-instruct-v1  - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)

* granite-13b-chat-v1   - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)

### REST Interface

````

https://us-south.ml.cloud.ibm.com/ml/v1-beta/generation/text?version=2023-05-29


{
  "model_id": "google/flan-ul2",
  "input": "${inputs:urlEncode()}",
  "parameters": {
    "decoding_method": "greedy",
    "max_new_tokens": 20,
    "min_new_tokens": 0,
    "stop_sequences": [],
    "repetition_penalty": 1
  },
  "project_id": "0ead8ec4-d137-4f9c-8956-50b0da4a7068" }

````


### References

* https://www.ibm.com/docs/en/watsonx-as-a-service?topic=models-
 
