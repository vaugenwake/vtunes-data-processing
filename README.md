# vTunes API Sample Data Import

This is a dump of some sample data to be used with the vTunes api project [here](https://github.com/vaugenwake/vtunes-api)

## Tools required
* AWS CLI
* Running DynamoDB instance either in AWS or in Docker with the project

## Importing data into docker table

### Import a single file:
```BASH
cd batch/users
aws --endpoint-url=http://localhost:8025 dynamodb batch-write-item --request-item=file://batch_1.json
```

### Import every file in directory:
This will popup reporting that items where written, you can hit `q` to continue to the next file if required
```BASH
cd batch/users
find . -name "batch_*.json" -exec sh -c 'aws --endpoint-url=http://localhost:8025 dynamodb batch-write-item --request-item file://$0' {} \;
```