# Use an image that includes essential build tools
FROM ubuntu:latest

# Set environment variables for Linux
ENV CONAN_CONFIG="-s compiler.libcxx=libstdc++11"
ENV FBXSDK_TARBALL="https://github.com/zellski/FBXSDK-Linux/archive/2019.2.tar.gz"

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    gcc \
    cmake \
    python3-pip \
    curl \
    zstd \
    git && \
    rm -rf /var/lib/apt/lists/*

# Install a specific version of Conan package manager
RUN pip3 install conan==1.42.1  # You can choose a different version if needed

# Add Conan remote
RUN conan remote add --force bincrafters https://api.bintray.com/conan/bincrafters/public-conan

# Clone the fbx2gltf repository
RUN git clone https://github.com/facebookincubator/FBX2glTF.git /FBX2glTF

# Navigate to project directory
WORKDIR /FBX2glTF

# Fetch and unpack FBX SDK
RUN curl -sL "${FBXSDK_TARBALL}" | tar xz && \
    mv FBXSDK-Linux-2019.2/sdk ./sdk

# Decompress the contents
RUN zstd -d -r --rm sdk

# Initialize & run build
RUN conan install . -if=build -s build_type=Release ${CONAN_CONFIG}
RUN conan build . -bf build

# Set the ENTRYPOINT to run the fbx2gltf executable
ENTRYPOINT [ "./build/FBX2glTF" ]
