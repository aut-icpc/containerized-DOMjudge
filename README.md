# Domjudge setup for Amirkabir ICPC contests

## Setup domserver (control plane)

1. First you need to setup docker on your ICPC main server. You might need to manually download docker and docker-compose packages and scp them to the server due to internet constraints.

2. Copy domserver directory to the server.

3. Replace `<rootpw>` and `<djpw>` fields inside the `docker-compose.yaml` with secure values.

4. `cd` inside the directory of `docker-compose.yaml` and run the following command: `docker compose up -d`

5. Run `docker ps` and verify if the domserver and mysql container are up and runnning (You can use `docker logs domserver`/`docker logs mariadb` command to inspect logs and check if there is any issues). The domserver has a health check component which shows if it's healthy (You might need to wait about a minute for it to become healthy).

6. Run `docker logs domserver` so that you can retreive `Initial admin password` to login as admin and `Initial judgehost password` in order to config judgehosts.

> **_NOTE:_**  It's recommended to test the latest version of docker images and replace `latest` tag with the actual tag to prevent further issues during the contest.

## Setup judgehosts (data plane)