from tensorflow/tensorflow:1.12.0-rc0-gpu-py3
run apt-get update && apt-get install -y  python-pil python-lxml python-tk git wget 
run pip install -U pip && pip install Cython contextlib2 jupyter matplotlib 
run mkdir /work
run wget https://github.com/protocolbuffers/protobuf/releases/download/v3.6.1/protobuf-all-3.6.1.tar.gz && tar zxvf protobuf-all-3.6.1.tar.gz && mv protobuf-3.6.1 /work/protobuf-3.6.1 && rm protobuf-all-3.6.1.tar.gz
run cd /work/protobuf-3.6.1 && ./configure && make -j15 && make check -j15 && make install -j15 && ldconfig
run rm /usr/bin/python && ln -s /usr/bin/python3.5 /usr/bin/python

# cocoapi commit id ed842bffd41f6ff38707c4f0968d2cfd91088688
run git clone --depth 1 -b master https://github.com/cocodataset/cocoapi.git /work/cocoapi && cd /work/cocoapi/PythonAPI && make
# tensorflow commit id 91b2debda873c77a5886ca76b3ca50cfbe8a1d4e
run git clone  --depth 1 --branch master https://github.com/tensorflow/models.git /work/models && cd /work/models
run cp -r /work/cocoapi/PythonAPI/pycocotools /work/models/research/
run cd /work/models/research/ && protoc object_detection/protos/*.proto --python_out=/work/models/research
add object_detection.ipynb /notebooks
ENV PYTHONPATH=$PYTHONPATH:/work/models/research/:/work/models/research/slim

