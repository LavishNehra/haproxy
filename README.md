# HAProxy Load Balancer

## Objective
Configure HAProxy as an HTTP load balancer for two Apache Tomcat servers using the Round Robin algorithm.

## Architecture
Client → HAProxy (Port 9090) → Tomcat 1 (Port 9091) / Tomcat 2 (Port 9092)

## Technologies
- HAProxy
- Docker
- Apache Tomcat 9
- Ubuntu Linux

## Configuration
- Frontend: `http_front`
- Backend: `tomcat_back`
- Load balancing algorithm: Round Robin
- Health checks: HTTP GET `/`
- Statistics dashboard: Port `8404`, path `/stats`

## Project Files
- `haproxy.cfg` — HAProxy configuration
- `ROOT.war` — Tomcat application
- `app/` — Application-related files

## Verification
Check the HAProxy service:

```bash
sudo systemctl status haproxy
```

Test the load balancer:

```bash
curl http://localhost:9090
```

Open the statistics dashboard at `http://localhost:8404/stats`.

**Note:** Both Tomcat backends must be running and reachable before load balancing can be verified successfully.
