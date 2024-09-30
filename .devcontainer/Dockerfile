FROM alpine

# NOTE: curl-dev is require to workaround unknown option failure from libcurl (assumed is old version)
RUN apk add --update clang llvm lld make cmake build-base ninja zip unzip curl-dev curl git bison flex

# Initial env variable for vcpkg path
ENV VCPKG_ROOT="/usr/local/vcpkg"
ENV PATH="${PATH}:${VCPKG_ROOT}"

# Install vcpkg
RUN git clone https://github.com/microsoft/vcpkg ${VCPKG_ROOT} \
    && ${VCPKG_ROOT}/bootstrap-vcpkg.sh

# Setup nxdk
RUN git clone --depth 1 --recurse-submodules https://github.com/XboxDev/nxdk.git /usr/src/nxdk
ENV NXDK_DIR=/usr/src/nxdk
ENV PATH="${NXDK_DIR}/bin:${PATH}"
