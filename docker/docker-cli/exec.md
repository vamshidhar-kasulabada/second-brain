# docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

The docker exec command is used to run a command inside a running Docker container.

command to open  a terminal session inside a container.
```bash
docker exec -it my_container bash
```


## Options

| Option      | Description                                     |
| ----------- | ----------------------------------------------- |
| `-it`       | Run interactively with a terminal (like `bash`) |
| `-d`        | Run the command in the background               |
| `--user`    | Specify user to run the command as              |
| `--env`     | Set environment variables                       |
| `--workdir` | Set working directory inside the container      |

