FROM python:3.4.3

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt update && \
    apt install -y g++ gcc gfortran wget curl && \
    wget http://www.netlib.org/lapack/lapack-3.6.1.tgz && \
    tar -xzvf lapack-3.6.1.tgz && \
    cd lapack-3.6.1 && \
    cp make.inc.example make.inc && \
    make blaslib && \
    make lapacklib && \
    make cblaslib && \
    make lapackelib && \
    cp ./librefblas.a /usr/lib/libblas.a && \
    cp ./liblapack.a /usr/lib/liblapack.a && \
    cp ./libcblas.a /usr/lib/libcblas.a && \
    cp ./liblapacke.a /usr/lib/liblapacke.a && \
    cp ./CBLAS/include/cblas*.h /usr/include/ && \
    cp ./LAPACKE/include/lapacke*.h /usr/include/ && \
    cd / && \
    rm -rf lapack-3.6.1* && \
    curl https://bootstrap.pypa.io/3.4/get-pip.py | python3.4 && \
    python3.4 -m pip install numpy==1.8.2 && \
    python3.4 -m pip install scipy==0.13.3 && \
    apt remove -y g++ gcc gfortran wget curl && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/* && \
    rm /usr/lib/libblas.a /usr/lib/liblapack.a /usr/lib/libcblas.a /usr/lib/liblapacke.a /usr/include/cblas*.h /usr/include/lapacke*.h
