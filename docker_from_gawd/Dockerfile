FROM nvcr.io/nvidia/pytorch:21.03-py3
#RUN conda install pytorch=1.4.0 torchvision torchaudio cudatoolkit=10.1 -c pytorch

RUN pip install   pytorch-lightning
RUN pip install -U git+https://github.com/albu/albumentations --no-cache-dir
RUN pip install opencv-python-headless
RUN pip install --no-cache-dir --upgrade pip

COPY requirements.txt /tmp/
RUN pip install --requirement /tmp/requirements.txt
COPY . /tmp/
RUN pip install opencv-python
RUN apt update && apt install -y libsm6 libxext6
RUN apt-get install -y libxrender-dev

RUN apt install -y p7zip-full p7zip-rar

ARG USER_ID
ARG GROUP_ID

RUN addgroup --gid $GROUP_ID user
RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID user
USER user

#RUN pip uninstall -y tb-nightly tensorboardX tensorboard
