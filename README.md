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

### Watson SSB SQL

````

CREATE TABLE `ssb`.`Meetups`.`watsonxresults` (
  `date` VARCHAR(2147483647),
  `x_global_transaction_id` VARCHAR(2147483647),
  `x_request_id` VARCHAR(2147483647),
  `cf_ray` VARCHAR(2147483647),
  `inputs` VARCHAR(2147483647),
  `created_at` VARCHAR(2147483647),
  `stop_reason` VARCHAR(2147483647),
  `x_correlation_id` VARCHAR(2147483647),
  `x_proxy_upstream_service_time` VARCHAR(2147483647),
  `message_id` VARCHAR(2147483647),
  `model_id` VARCHAR(2147483647),
  `invokehttp_request_duration` VARCHAR(2147483647),
  `message` VARCHAR(2147483647),
  `uuid` VARCHAR(2147483647),
  `generated_text` VARCHAR(2147483647),
  `transaction_id` VARCHAR(2147483647),
  `tokencount` VARCHAR(2147483647),
  `generated_token` VARCHAR(2147483647),
  `ts` VARCHAR(2147483647),
  `eventTimeStamp` TIMESTAMP(3) WITH LOCAL TIME ZONE METADATA FROM 'timestamp',
  WATERMARK FOR `eventTimeStamp` AS `eventTimeStamp` - INTERVAL '3' SECOND
) WITH (
  'deserialization.failure.policy' = 'ignore_and_log',
  'properties.request.timeout.ms' = '120000',
  'format' = 'json',
  'properties.bootstrap.servers' = 'kafka:9092',
  'connector' = 'kafka',
  'properties.transaction.timeout.ms' = '900000',
  'topic' = 'watsonxaillm',
  'scan.startup.mode' = 'group-offsets',
  'properties.auto.offset.reset' = 'earliest',
  'properties.group.id' = 'allwatsonx1'
)


````

### Videos

https://www.youtube.com/watch?v=RPz7Xm4fLF4


### Models

* google/flan-ul2

* google/flan-t5-xxl

* ibm/granite-13b-instruct-v1  - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)

* ibm/granite-13b-chat-v1   - IBM Granite models (granite-13b-instruct-v1, granite-13b-chat-v1)


### Example Query Input

````

{"inputs":"Please answer to the following question. What is the capital of the United States?"}

````


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
* https://www.ibm.com/docs/en/watsonx-as-a-service?topic=models-prompt-tips
* https://www.ibm.com/docs/en/watsonx-as-a-service?topic=tips-sample-prompts

### Introduction



Real-time Integration of WatsonX.AI Foundation Models with NiFi


Hi, I am Timothy Spann, Principal Developer Advocate for Streaming at Cloudera.   

Today I will show you how to use Cloudera DataFlow powered by Apache NiFi to interact with IBM WatsonX.AI foundation large language models in real-time.   We can work with any of the foundation models such as Google FLAN T5 XXL or  IBM Granite models.

I’ll show you how easy it is to build a real-time data pipeline feeding your like Slack and mobile applications questions directly to secure WatsonX.AI models running in IBM Cloud.   We will handle all the security, management, lineage and governance with Cloudera Data Flow.   As part of decision making we can choose different WatsonX.AI models on the fly based on what type of prompt it is.   For example, if we want to continue a sentence versus answering a question I can pick different models.   For questions answering Google FLAN T5 XXL works well.   If I want to continue sentences I would use one of the IBM Granite models.

You will notice how amazingly fast the WatsonX.AI models return the results we need.   I do some quick enrichment and transformation and then send them out their way to Cloudera Apache Kafka to be used for continuous analytics and distribution to many other applications, systems, platforms and downstream consumers.   We will also output our answers to the original requester which could be someone in a Slack channel or someone in an application.   All of this happens real-time, with no code, full governance, lineage, data management and security at any scale and on any platform.   

The power of IBM and Cloudera together in private, public and hybrid cloud environments for real-time data and AI is just getting started.   Try it today.

### IBM + Cloudera for Apache Kafka
https://blog.cloudera.com/ibm-technology-chooses-cloudera-as-its-preferred-partner-for-addressing-real-time-data-movement-using-kafka/

### Video
https://www.youtube.com/watch?v=RPz7Xm4fLF4&t=6s

### Source Code
https://github.com/tspannhw/FLaNK-watsonx.ai

### Models
https://www.ibm.com/docs/en/watsonx-as-a-service?topic=models-



 
