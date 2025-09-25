# Use Ollama Docker Image as the base
FROM ollama/ollama:0.12.1

# Pre-pull models during image build
RUN ollama serve & \
    sleep 10 && \
    ollama pull tinyllama && \
    pkill ollama

# Ollama uses the port 11434
EXPOSE 11434

CMD ["ollama", "serve"]