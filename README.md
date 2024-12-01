# Docker Compose Monitoring Stack Using Grafana, Prometheus, cAdvisor, and Node Exporter

This setup uses Docker Compose to deploy a monitoring stack consisting of **Grafana**, **Prometheus**, **cAdvisor**, and **Node Exporter**. The stack provides real-time insights into your containerized applications and system performance. Grafana is used for visualizing metrics, Prometheus for scraping and storing metrics, cAdvisor for monitoring container performance, and Node Exporter for system-level metrics.

## Prerequisites

Before running the Docker Compose setup, ensure you have the following installed:

1. **Docker**:
   - Docker is required to build and run the containers.
   - You can download Docker from [here](https://www.docker.com/get-started).

2. **Docker Compose**:
   - Docker Compose is a tool for defining and running multi-container Docker applications.
   - Starting with Docker version 20.10.0, Docker Compose is included as part of Docker Desktop. If you need to install it separately, follow the instructions from the [official Docker Compose documentation](https://docs.docker.com/compose/install/).

3. **A terminal**:
   - You should be familiar with using a terminal or command-line interface.

## How to Run the Application Using Docker Compose

1. **Clone the Repository**

    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```

2. **Choose the Application You Want to View**

   Uncomment the port of the application you want to view in the `docker-compose.yml` file.

   For example:
   - Grafana, which is used for the monitoring dashboard, uses port `3000`.

3. **Start the Application**

   Build and start the application containers by running:

   ```bash
   docker compose up -d
   ```

   It will pull the necessary images if they are not present locally and run the containers in detached mode.
    
4. **View the Application**

   Open your browser and go to `http://localhost:{{port-of-the-app-you-want-to-view-and-have-uncommented}}`.

   For example:
   - Grafana (monitoring dashboard) is accessible at: http://localhost:3000.

## Importing a Dashboard into Grafana

After the Grafana container is up and running, you can import a pre-built dashboard to visualize your metrics.

1. Open your browser and go to the Grafana dashboard URL (e.g., http://localhost:3000).

2. Log in to Grafana with the default credentials:
   
   Username: `admin`

   Password: `admin`

   You will be prompted to change the password after the first login.

3. Add Prometheus as Data Source
   To add Prometheus as a data source:
   - In the left-hand menu, click on the **gear icon** (⚙️) to go to **Configuration**.
   - Click on **Data Sources**.
   - Click on **Add data source**.
   - Select **Prometheus** from the list of available data sources.
   - In the **HTTP URL** field, enter the address of your Prometheus container. By default, it will be `http://prometheus:9090` (if you're using the provided `docker-compose.yml` file).
   - Click **Save & Test** to verify the connection.

   Prometheus is now configured as a data source in Grafana.
   
4. Import a dashboard:
    - In the left-hand menu, click on the **Plus** icon (`+`) and select **Import Dashboard**.
    - Enter the **Dashboard ID** from [Grafana's official dashboard repository](https://grafana.com/grafana/dashboards) or upload a **JSON file** for the dashboard.
       - For example, you can use json file included in this repository.
    - Click **Load**.

5. Select the correct Prometheus data source (usually prometheus) and click "Import".
    
   The dashboard will now be available for you to monitor your container metrics and system performance!
