# Build Poetry Docker Image

## Overview

This Docker image provides a Python 3.11 development environment with Poetry for dependency management and common Python development tools.

## Base Image

- **Base:** `python:3.11-slim-bookworm`
- **OS:** Debian Bookworm (slim variant)
- **Python Version:** 3.11

## Installed Components

### System Packages

- **git** - Version control system for cloning repositories and managing code
- **curl** - Tool for downloading files and making HTTP requests
- **build-essential** - Compilation tools (GCC, make, etc.) required for building Python packages with C extensions

### Python Tools

#### Poetry
- **Installation Path:** `/opt/poetry`
- **Purpose:** Modern dependency management and packaging tool for Python projects
- **Added to PATH:** Yes

#### Development and Testing Tools
- **pytest** - Testing framework for writing and running unit tests
- **bandit** - Security linter for identifying common security issues in Python code
- **pylint** - Static code analyzer for code quality and style checks

## Configuration

- **Working Directory:** `/app`
- **PATH:** Extended to include `/opt/poetry/bin`

## Usage

### Building the Image

```bash
docker build -t build-poetry -f build-poetry/Dockerfile .
