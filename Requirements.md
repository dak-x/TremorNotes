# Requirements

Streaming Fashion:

# Configuration Options
- AWS Cred. (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, and AWS_REGION)
- Defaults. (Regions, etc)



# Different Configuration Proposals:

1. Config Ex1:
   Map the auth tokens to the explicit env variable. This can support multiple s3 connectors in such a way.
   ```
   AWS_ACCESS_TOKEN: <ENV VAR>
   AWS_SECRET_KEY: <ENV VAR>
   AWS_REGION: <ENV VAR>
   
   max-client: <Number>
   ```

2. Config-Ex2:
    Fixed default bucket names.
    Can override bucket name for smaller quantity of event.
    No ability to manipulate bucket properties.
   ```
   AWS_ACCESS_TOKEN: <ENV VAR>
   AWS_SECRET_KEY: <ENV VAR>
   AWS_REGION: <ENV VAR>
   
   max-clients: <Number>
   bucket: <bucket name>
   event-threshold: <Size>
   ```

   ### Questions: 
   1. 
   2. What is the max size we should pick for multipart uploads.
   3. Size splitting. <- Add a size splitting pre-processors.
   4. Timeout :- connector-sink.
   5. Just go with name changing scheme.
   6. Elastic.rs Abstraction for client pool
   7. 


## Operation Information:
1. Define a seperate structure Operation Vars inside the Event Payload.
   - Pros:
     - Full Control over the Event.
   - Cons:
     - Too Verbose
     - Have to Write more Script for common case. Can be avoided by sane defaults.
     - Too much copying of the Meta-Data for each event.

2. Define the required parameters as Meta Information:
   - Pros:
     - Full Control over the Event. 
     - Semantically makes more sense to include this info in Meta section. No changes for the user.
   - Cons:
     - Similar to #1.
   
