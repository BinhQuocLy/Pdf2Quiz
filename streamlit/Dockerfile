FROM ubuntu:20.04

SHELL ["/bin/bash", "-c"]

WORKDIR /app

RUN apt update -y && apt upgrade -y
RUN apt install sudo
RUN sudo apt install -y software-properties-common
RUN sudo add-apt-repository -y ppa:deadsnakes/ppa
RUN sudo apt update -y
RUN sudo apt install -y python3.8
RUN sudo apt install -y ffmpeg libsm6 libxext6 poppler-utils tesseract-ocr
RUN sudo apt install -y python3-pip

COPY requirements.txt .

RUN pip install -r requirements.txt
RUN spacy download en_core_web_lg
RUN spacy download en_core_web_sm

COPY . .

RUN rm -rf /var/lib/apt/lists/*

CMD ["streamlit", "run", "app.py"]
