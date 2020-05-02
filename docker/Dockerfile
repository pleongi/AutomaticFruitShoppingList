# Copyright 2018 The TensorFlow Authors. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# #==========================================================================

FROM tensorflow/tensorflow:nightly-devel-py3

# Get the tensorflow models research directory, and move it into tensorflow
# source folder to match recommendation of installation
RUN git clone --branch r1.13.0 --depth 1 https://github.com/tensorflow/models.git && \
    mv models /tensorflow/models



ARG DEBIAN_FRONTEND=noninteractive


# Install pycocoapi
#RUN git clone --depth 1 https://github.com/cocodataset/cocoapi.git && \
#    cd cocoapi/PythonAPI && \
#    make -j8 && \
#    cp -r pycocotools /tensorflow/models/research && \
#    cd ../../ && \
#    rm -rf cocoapi


RUN python3 -m pip --no-cache-dir install --upgrade \
    pip \
    setuptools
# Install object detection api dependencies
RUN pip install Cython && \
    pip install contextlib2 && \
    pip install beautifulsoup4 && \
    pip install opencv-python && \
    pip install lxml && \
    pip install matplotlib

# Install the Tensorflow Object Detection API from here
#RUN pip install -U --pre tensorflow=="2.*"

# Get protoc 3.0.0, rather than the old version already in the container
RUN curl -OL "https://github.com/google/protobuf/releases/download/v3.0.0/protoc-3.0.0-linux-x86_64.zip" && \
    unzip protoc-3.0.0-linux-x86_64.zip -d proto3 && \
    mv proto3/bin/* /usr/local/bin && \
    mv proto3/include/* /usr/local/include && \
    rm -rf proto3 protoc-3.0.0-linux-x86_64.zip

# Run protoc on the object detection repo
RUN cd /tensorflow/models/research && \
    protoc object_detection/protos/*.proto --python_out=.

#RUN cd / && tf_upgrade_v2 --intree /tensorflow/models/research/object_detection/ --outtree /tensorflow/models/research/object_detection/
# Set the PYTHONPATH to finish installing the API
ENV PYTHONPATH $PYTHONPATH:/tensorflow/models/research:/tensorflow/models/research/slim


RUN pip install /tensorflow/models/research/

#ENV cd /tensorflow/models/research && python setup.py build
#ENV cd /tensorflow/models/research && python setup.py install

# Install wget (to make life easier below) and editors (to allow people to edit
# the files inside the container)
#RUN apt-get install -y wget vim emacs nano

WORKDIR /tensorflow


EXPOSE 8888
CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/", "--ip=0.0.0.0", "--port=8888", "--no-browser"]