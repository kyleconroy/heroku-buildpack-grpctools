# Run these commands on a dyno to build the needed libs and binaries
curl -LO https://github.com/grpc/grpc/archive/release-0_11_1.tar.gz
curl -LO https://github.com/google/protobuf/archive/v3.0.0-alpha-4.1.tar.gz
tar -zxvf release-0_11_1.tar.gz
tar -zxvf v3.0.0-alpha-4.1.tar.gz
mkdir -p /app/dest

# Protobug
pushd protobuf-3.0.0-alpha-4.1
./autogen.sh
./configure
make install prefix=/app/dest
popd

# Make sure GRPC can find the protobuf libs
export LD_LIBRARY_PATH="/app/dest/lib/:$LD_LIBRARY_PATH"
export PATH="/app/dest/bin/:$PATH"

pushd grpc-release-0_11_1
make install prefix=/app/dest

# Download
curl -OL https://raw.githubusercontent.com/scottmotte/srvdir-binary/master/srvdir.tar.gz 
tar -zxvf srvdir.tar.gz
./srvdir
