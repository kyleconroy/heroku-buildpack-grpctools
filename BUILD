# Run these commands on a dyno to build the needed libs and binaries
git clone https://github.com/grpc/grpc.git

mkdir -p /app/dest

cd grpc
git checkout release-0_11_1
git submodule update --init
make
make install prefix=/app/dest

cd third_party/protobuf
make install prefix=/app/dest

cd ~
tar czf grpc.tar.gz -C /app/dest .

# Download
curl -OL https://raw.githubusercontent.com/scottmotte/srvdir-binary/master/srvdir.tar.gz 
tar -zxvf srvdir.tar.gz
./srvdir
