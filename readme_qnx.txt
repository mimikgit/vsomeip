Build instructions for QNX 7.1

# source the QNX environment script
source <path-to-qnxsdp-env.sh>/qnxsdp-env.sh

# Create a workspace
mkdir ~/vsomeip_workspace
WORKSPACE=~/vsomeip_workspace

# Build and install boost
cd $WORKSPACE
git clone https://gitlab.com/qnx/libs/boost.git && cd boost
git checkout QNX_7.1_v1.63.0
git submodule update --init --recursive
cd tools/build
git apply ../../boost_tools_build_qnx.patch
cd -
mkdir -p ./boost/utility
cp -r ./libs/utility/include/boost/utility/detail ./boost/utility
make install -j4

# Get googletest
cd $WORKSPACE
git clone https://gitlab.com/qnx/libs/googletest.git
export GTEST_ROOT=$WORKSPACE/googletest

# Build and install vsomeip
git clone -b mimik-master https://github.com/mimikgit/vsomeip.git && cd vsomeip/build_qnx

# Before building, look at $WORKSPACE/vsomeip/build_qnx/common.mk
# set TEST_IP_MASTER to the target ip address
# set TEST_IP_SLAVE to the host PC ip address for tests
make install -j4

