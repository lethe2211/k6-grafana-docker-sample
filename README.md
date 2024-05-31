# Stress test environment for me

## Dependencies

1. Docker >= 24

## How to use it

1. Modify `targetapp` directory so that it will run a target web application. Modify `compose.yml` according to the port number you want to expose.
2. Modify the k6 test scenario in `scripts/test.js`. You can access the target app with the hostname: `targetapp`
    Ref: https://k6.io/docs/
3. Construct the environment
    ```bash
    docker compose up --build -d
    ```
    You can now access `localhost:3000` for Grafana and `localhost:9000` for Prometheus
4. Set up the dashboard
    1. Select the datasource https://zenn.dev/nyama39/articles/3ef0d951e2aa30#grafana-%E3%81%AE%E3%83%87%E3%83%BC%E3%82%BF%E3%82%BD%E3%83%BC%E3%82%B9%E3%81%AB-prometheus-%E3%82%92%E8%BF%BD%E5%8A%A0%E3%81%99%E3%82%8B
    2. Create a dashboard https://zenn.dev/nyama39/articles/3ef0d951e2aa30#%E3%83%80%E3%83%83%E3%82%B7%E3%83%A5%E3%83%9C%E3%83%BC%E3%83%89%E3%81%AE%E4%BD%9C%E6%88%90
5. Run the tests
    ```bash
    docker compose run k6 -o experimental-prometheus-rw run /scripts/test.js
    ```
