# AI-at-Education

## Project Breakdown
This application is built using VueJS and Ollama backend. 

- Frontend and backend are containerized
- The user can use a single `docker-compose up` to run the application
- The default model is `phi3:latest`
- Users can pull other models using `docker exec ollama ollama pull <model-name>`

## Project Goal
The goal of this project is to create a simple webpage where the user can interact with an LLM which runs locally on the machine.
The model behaves as an AI tutor that can help understanding different concepts, such as:
  1. Math
  2. Programming
  3. World facts
  4. and more

The whole application is containerized, which means that the user don't have to install any dependencies on the machine. By default the model uses the CPU to generate responses.
If someone has a capable GPU, a small change in the `docker-compose.yaml` file can be done to run the model using the GPU. After the `endpoint` key we can add:

```yaml
    ...
    ...
    entrypoint: ["/usr/bin/bash", "run-ollama.sh"] 
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]
    ...
    ...
```
