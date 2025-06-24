FROM pytorch/pytorch:latest
ARG DEBIAN_FRONTEND=noninteractive
COPY requirements.txt /requirements.txt
RUN apt-get -y update &&\
    apt-get -y full-upgrade &&\
    apt-get -y install python3-pip python3-opencv ffmpeg git libsm6 libxext6 wget &&\
    python3 -m pip install --upgrade pip &&\
    python3 -m pip install -r /requirements.txt --no-cache-dir --root-user-action=ignore &&\
    git clone https://github.com/facebookresearch/sam2.git &&\
    cd sam2 &&\
    python3 -m pip install -e ".[notebooks]"
WORKDIR /torch
CMD ["jupyter", "notebook", "--notebook-dir='/torch/notebooks'", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]