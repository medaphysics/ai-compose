FROM python:3.11-slim

WORKDIR /app

RUN apt-get update && apt-get install -y git && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y \
    python3-pip \
    python3-dev \
    libsdl2-dev \
    libsdl2-image-dev \
    libsdl2-mixer-dev \
    libsdl2-ttf-dev \
    libsm6 \
    libxext6 \
    libxrender-dev \
    python3-tk \       
    tk-dev \            
    && rm -rf /var/lib/apt/lists/*

# Gerekli sistem kütüphanelerini yükle
RUN apt-get update && apt-get install -y \
    libgl1 \
    libx11-6 \
    libasound2 \
    pulseaudio \
    && pip install pygame

    
RUN pip install PyOpenGL PyOpenGL_accelerate \
    && pip install pygame


RUN apt-get install -y libasound2 libasound2-dev

# GUI test aracı olarak x11-apps kurulabilir (isteğe bağlı)
RUN apt update && apt install -y x11-apps

# Anlık history yazımı için:
ENV PROMPT_COMMAND="history -a"

# 1) Gereksinimleri yükle
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# 2) Logging kodunu içeren script'i kopyala
#COPY ./files/logging_app.py ./

# 3) Unbuffered modda çalıştır (-/u ile stdout’u hemen bas)
# CMD ["python", "-u", "logging_app.py -v"]

ENTRYPOINT ["/bin/bash", "-c", "while true; do sleep 1000; done"]
