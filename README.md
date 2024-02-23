## Homework Short Description
 A REST API with two POST endpoints:
 
 First POST endpoint receives a JSON in the form of a document with two fields: a pool-id (numeric) and a pool-values (array of values) and is meant to append (if pool already exists) or insert (new pool) the values to the appropriate pool (as per the id).
 The response from the append is a status field confirming "appended" or "inserted"
 
 Second POST is meant to query a pool, the two fields are pool-id (numeric) identifying the queried pool, and a quantile (in percentile form).
 The response from the query has two fields: the calculated quantile and the total count of elements in the pool

## Installation After unzip file
$ cd code

$ pip install -r requirements.txt

$ uvicorn main:app --host 127.0.0.1 --port 8000 --reload


## Program structure
```
.  
├── src  
│   ├── const.py    		// file contains constant variables
│   └── dto.py    		// file contains schema/ model supporting api
│   └── file_handling.py	// file contains functions supporting data persisted
├── data   					// folder contains pool data in form of json documents
├── main.py					// main program
├── test.py					// test cases
├── README.md
└── requirements.txt    	// pip install
```

API will start and be available at http://127.0.0.1:8000.

## Description

API 1: http://127.0.0.1:8000/pool/update

curl --location 'http://127.0.0.1:8000/pool/update' \
--header 'Content-Type: application/json' \
--data '{
    "poolId": 105,
    "poolValues": [1,2,3,4,5]
}'

API 2: http://127.0.0.1:8000/pool/query

curl --location 'http://127.0.0.1:8000/pool/query' \
--header 'Content-Type: application/json' \
--data '{
"poolId": 105,
"percentile": 0.5 
}'


