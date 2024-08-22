# milvus-vector-db

Helm chart for deploying Milvus Vector DB service.

## Install the Chart

To install the chart, run the following:

```console
cd ${GenAIInfro_repo}/helm-charts/common
helm install milvus-vector-db milvus-vector-db
```

## Verify

To verify the installation, run the command `kubectl get pod` to make sure all the milvus pods are runinng.

Then run the command `kubectl port-forward svc/milvus-vector-db 19530:19530` to expose the milvus vector db service for access.

Open another terminal and run the following commands:
```
export MILVUS_URI="http://milvus-vector-db:19530"
curl --request GET --url "${MILVUS_URI}/v1/vector/collections" --header 'accept: application/json' --header 'content-type: application/json'
```

## Values

| Key                          | Type   | Default                    | Description            |
| ---------------------------- | ------ | -------------------------- | ---------------------- |
| image                        | string | `"milvusdb/milvus:v2.4.6"` |                        |
| service.grpcPort             | string | `"19530"`                  | The aRPC port          |
| service.apiPort              | string | `"9091"`                   | The RESTful API port   |
