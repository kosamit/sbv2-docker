FROM pytorch/pytorch:2.2.2-cuda12.1-cudnn8-runtime
ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt update && apt install -y build-essential libssl-dev libffi-dev cmake git wget ffmpeg nvidia-cuda-toolkit libatlas-base-dev gfortran
RUN pip3 uninstall -y cmake

WORKDIR /app
ENV LD_LIBRARY_PATH /opt/conda/lib/python3.10/site-packages/nvidia/cublas/lib:/opt/conda/lib/python3.10/site-packages/nvidia/cudnn/lib:${LD_LIBRARY_PATH}

RUN git clone https://github.com/litagin02/Style-Bert-VITS2.git -b 2.6.0 --depth 1 .

# Pythonの依存関係をインストール
RUN pip install -r requirements.txt

# initialize
RUN python initialize.py --skip_default_models
