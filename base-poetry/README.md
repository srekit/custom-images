# Base Poetry

A Docker image based on Python `3.14 slim`, configured with a non-root user for running Poetry applications.

## Features:

- Base Image: python:3.14-slim
- Non-root User: Configurable user and group for secure execution
- Customizable: Build arguments for user configuration and working directory

## Build Arguments

| Argument  | Default Value | Description                    | 
|-----------|---------------|--------------------------------|
| USERNAME  | poetry        | Name of the non-root user      |
| USER_UID  | 1000          | User ID for the created user   |
| USER_GID  | 1000          | Group ID for the created group |
| WORKDIR   | /app          | Working directory path         |


## Security Considerations

- Runs as non-root user by default
- Uses UID/GID 1000 which aligns with common Linux user IDs
- Proper file ownership set for working directory
