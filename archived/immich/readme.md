# outline

## Redis Sentinel Configuration

1. Create base64 encoded Redis configuation
    ```sh
    echo -n '{"db":15,"sentinels":[{"host":"redis-node-0.redis-headless.database.svc.cluster.local","port":26379},{"host":"redis-node-1.redis-headless.database.svc.cluster.local","port":26379},{"host":"redis-node-2.redis-headless.database.svc.cluster.local","port":26379}],"name":"redis-master"}' \
        | base64 -w 0
    ```

    Alternatively, if using a single dragonfly instance:
    ```sh
    echo -n '{"sentinels":[{"host":"immich-dragonfly.media.svc.cluster.local","port":6379}],"name":"redis-sentinel"}' | base64 -w 0
    ```

2. Use this base64 encoded string in the Kubernetes secret
    ```yaml
    REDIS_URL: ioredis://eyJkYiI6MTUsInNlbnRpbmVscyI6W3siaG9zdCI6InJlZGlzLW5vZGUtMC5yZWRpcy1oZWFkbGVzcy5kYXRhYmFzZS5zdmMuY2x1c3Rlci5sb2NhbCIsInBvcnQiOjI2Mzc5fSx7Imhvc3QiOiJyZWRpcy1ub2RlLTEucmVkaXMtaGVhZGxlc3MuZGF0YWJhc2Uuc3ZjLmNsdXN0ZXIubG9jYWwiLCJwb3J0IjoyNjM3OX0seyJob3N0IjoicmVkaXMtbm9kZS0yLnJlZGlzLWhlYWRsZXNzLmRhdGFiYXNlLnN2Yy5jbHVzdGVyLmxvY2FsIiwicG9ydCI6MjYzNzl9XSwibmFtZSI6InJlZGlzLW1hc3RlciJ9
    ```
