FROM python:3.11-slim

WORKDIR /app

RUN apt-get update && apt-get install -y git tree && rm -rf /var/lib/apt/lists/*

RUN pip install openai
RUN pip install python-dotenv




# 1) Gereksinimleri yükle
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# 2) Logging kodunu içeren script'i kopyala
#COPY ./files/logging_app.py ./

# 3) Unbuffered modda çalıştır (-/u ile stdout’u hemen bas)
# CMD ["python", "-u", "logging_app.py -v"]

ENTRYPOINT ["/bin/bash", "-c", "while true; do sleep 1000; done"]
