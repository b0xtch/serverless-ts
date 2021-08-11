                              +----------+
                        +----> Primary DB|
       +----------+     |     +----------+     +----------------+      +------------+    +-----+
                  |     +                      |                |      |            |    |     |
          Lambda  +----->                +----->  SQS-Queue #1  +------>   Lambda   +---->Redis|
                  |     +                |     |                |      |            |    |     |
       +----------+     |                |     +----------------+      +------------+    +-----+
                        |    +-----------+
                        |    |           |
                        +---->   SNS     |
                             |           |
                             +-----------+
                                         |     +----------------+
                                         |     |                |
                                         +-----> SQS-Queue #2   | <------ Notify
                                               |                |
                                               +----------------+

Plug will be sending requests off to the api gateway which then proxies the request to our aws lambda

The server will then translate the query to the data source in the schema

server will check if the type is cacheable (cachecontrole) if so it will look in our redir endpoint for cached response

if there is no cached response it will send of a request to xtc in this case. again it will check if the response is cacheable and store the results in redis

yarn init -y
yarn add --dev typescript
npx tsc --init
yarn add --dev @types/node ts-node-dev ts-node ts-loader typescript
yarn add typescript prom-client axios express
mkdir src
# serverless-ts
