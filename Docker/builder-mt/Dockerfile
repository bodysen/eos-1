FROM eosio/builder as builder

# Added for pubsub plugin
RUN git clone --depth 1 -b 1.1.7 https://github.com/google/snappy.git \
    && cd snappy \ 
    && mkdir build \
    && cd build \
    && cmake ../ \
    && make install \
    && cd ../../ && rm -rf snappy 

# zookeeper 
COPY cppunit.m4 /usr/local/share/aclocal/
COPY zookeeper.jute.c /tmp/
COPY zookeeper.jute.h /tmp/
COPY zookeeper-release-3.5.4.tar.gz /tmp/
#RUN wget https://github.com/apache/zookeeper/archive/release-3.5.4.tar.gz \
RUN cd /tmp \
    && tar -zxf zookeeper-release-3.5.4.tar.gz \
    && cd zookeeper-release-3.5.4/src/c \
    && ACLOCAL="aclocal -I /usr/local/share/aclocal" autoreconf -if \
    && mkdir generated \
    && cp /tmp/zookeeper.jute.* generated/ \
    && ./configure \
    && make \
    && make install \
    && cd ../../../ \
    && rm -rf zookeeper-release-3.5.4

# jasson
RUN git clone --depth 1 -b v2.11 https://github.com/akheron/jansson.git \
    && cd jansson \ 
    && mkdir build \
    && cd build \
    && cmake ../ \
    && make install \
    && cd ../../ && rm -rf jansson 

# librdkafka 
RUN git clone --depth 1 -b v0.11.4 https://github.com/edenhill/librdkafka.git \
    && cd librdkafka \ 
    && ./configure --enable-static \
    && make \
    && make install \
    && cd ../ && rm -rf librdkafka 

