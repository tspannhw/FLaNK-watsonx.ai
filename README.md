# FLaNK-watsonx.ai

FLaNK Stack with watsonx.ai for google/flan-ul2, google/flan-t5-xxl, Granite and other foundation models


### Apache NiFi Flow

![img](https://github.com/tspannhw/FLaNK-watsonx.ai/blob/main/images/watsonainifi.jpg?raw=true)

![img](https://github.com/tspannhw/FLaNK-watsonx.ai/blob/main/images/watsonaixflow2.jpg?raw=true)

![img](https://github.com/tspannhw/FLaNK-watsonx.ai/blob/main/images/watsonflow3.jpg?raw=true)


### Output to Slack

![img](https://github.com/tspannhw/FLaNK-watsonx.ai/blob/main/images/watsonllmslack.png?raw=true)


### Output to Apache Kafka

![img](https://github.com/tspannhw/FLaNK-watsonx.ai/blob/main/images/watsonxaikafkaresults.png?raw=true)


### Videos

https://www.youtube.com/watch?v=RPz7Xm4fLF4


### Models

* google/flan-ul2

* google/flan-t5-xxl

* granite-13b-instruct-v1  - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)

* granite-13b-chat-v1   - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)


### REST Interface

````
Get identity Token

https://iam.cloud.ibm.com/identity/token

grant_type=urn%3Aibm%3Aparams%3Aoauth%3Agrant-type%3Aapikey&apikey=<Get Your Own API Key at IBM Cloud>


Call Model after identity grant using Identity Token

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
  "project_id": "Get-Your-IBM-Cloud-ProjectID" }

````


### References

* https://www.ibm.com/docs/en/watsonx-as-a-service?topic=models-
 
