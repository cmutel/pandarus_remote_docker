# Dockerfile for pandarus_remote

Based on the [ContinuumIO miniconda3 image](https://github.com/ContinuumIO/docker-images/blob/master/miniconda3/Dockerfile).

## What it Gives You

* Miniconda Python 3.6 & pandarus_remote

## Usage

If you want to preserve your pandarus results (high recommended), you will need to create two docker volumes:

    docker volume create pr-log
    docker volume create pr-data

Then, when running the docker volume, you will need to forward whatever port you are listening on (here 9876) to port 5000 in the docker volume. You will also need to mount the two created volumes:

    docker run -d \
        -p 5000:5000 \
        --mount source=pr-log,target=/root/.cache/PandarusRemote/log \
        --mount source=pr-data,target=/root/.local/share/PandarusRemote \
        pandarus_remote_docker
