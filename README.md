# workshop_docker

This is a simple Streamlit app running inside a Docker container.

# My First App

This is a simple Streamlit app running inside a Docker container.

## Prerequisites

- Docker installed on your system

## Getting Started

### 1. Build the Docker Image

```sh
docker build -t my-streamlit-app .
```

### 2. Run the Container

```sh
docker run -d -p 8501:8501 --name my-streamlit-container my-streamlit-image
```

### 3. Access the App

Open your browser and go to: [http://localhost:8501](http://localhost:8501)

## Project Structure

```
.
├── Dockerfile
├── app.py
├── pyproject.toml
└── README.md
```

## Dockerfile

```dockerfile
# Download python image
FROM python:3.12

RUN pip install poetry

COPY . /src

WORKDIR /src

RUN poetry install --no-root

EXPOSE 8501

ENTRYPOINT ["poetry", "run", "streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

## app.py

```python
import streamlit as st
import pandas as pd
 
st.write("""
# My first app
Hello *world!*
""")
```

## Additional Notes

- Ensure Docker is running before executing the commands.
- You can modify `app.py` to add more features.
- If you need to stop the container, use `Ctrl+C` in the terminal where it's running or run:

```sh
docker ps  # Find the container ID
docker stop <container_id>
```

