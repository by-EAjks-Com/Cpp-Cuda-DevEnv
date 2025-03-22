#   by-EAjks.Com Development Environments
#   Copyright (C) 2025-2025 Andrea and Eric DELAGE <Contact@by-EAjks.Com>
#
#   This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <https://www.gnu.org/licenses/>.

ARG IMAGE_REPOSITORY
ARG IMAGE_NAME
ARG IMAGE_SHA

FROM ${IMAGE_REPOSITORY}/${IMAGE_NAME}@${IMAGE_SHA}

LABEL maintainer="by-EAjks.Com <Contact@by-EAjks.Com>"

ENV DEBIAN_FRONTEND=noninteractive

# Add Intel OneAPI support

RUN apt-get update \
 && apt-get install --yes --no-install-recommends \
        git=1:2.43.0-1ubuntu7.2 \
        git-flow=1.12.3-3 \
        cmake=3.28.3-1build7 \
        ninja-build=1.11.1-2 \
        doxygen=1.9.8+ds-2build5 \
        graphviz=2.42.2-9ubuntu0.1 \
        build-essential=12.10ubuntu1 \
        llvm=1:18.0-59~exp2 \
        clang=1:18.0-59~exp2 \
        clang-format=1:18.0-59~exp2 \
        clang-tidy=1:18.0-59~exp2 \
        clang-tools=1:18.0-59~exp2 \
        lld=1:18.0-59~exp2 \
        intel-oneapi-common-licensing-2025.1=2025.1.0-359 \
        intel-oneapi-dpcpp-cpp-2025.1=2025.1.0-973 \
        libssl-dev=3.0.13-0ubuntu3.5 \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*

RUN apt-mark hold \
        git \
        git-flow \
        cmake \
        ninja-build \
        doxygen \
        graphviz \
        build-essential \
        llvm \
        clang \
        clang-format \
        clang-tidy \
        clang-tools \
        lld \
        intel-oneapi-common-licensing-2025.1 \
        intel-oneapi-dpcpp-cpp-2025.1 \
        libssl-dev

# Add Nvidia CUDA support

RUN apt-get update \
 && apt-get install --yes --no-install-recommends \
        cuda-cudart-dev-12-8=12.8.90-1 \
        cuda-command-line-tools-12-8=12.8.1-1 \
        cuda-minimal-build-12-8=12.8.1-1 \
        cuda-libraries-dev-12-8=12.8.1-1 \
        cuda-nvml-dev-12-8=12.8.90-1 \
        cuda-nvprof-12-8=12.8.90-1 \
        libnpp-dev-12-8=12.3.3.100-1 \
        libcublas-dev-12-8=12.8.4.1-1 \
        libcusparse-dev-12-8=12.5.8.93-1 \
        libnccl-dev=2.26.2-1+cuda12.8 \
        cuda-nsight-compute-12-8=12.8.1-1 \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*

RUN apt-mark hold \
        cuda-cudart-dev-12-8 \
        cuda-command-line-tools-12-8 \
        cuda-minimal-build-12-8 \
        cuda-libraries-dev-12-8 \
        cuda-nvml-dev-12-8 \
        cuda-nvprof-12-8 \
        libnpp-dev-12-8 \
        libcublas-dev-12-8 \
        libcusparse-dev-12-8 \
        libnccl-dev \
        cuda-nsight-compute-12-8

ENV LIBRARY_PATH=/usr/local/cuda/lib64/stubs${LIBRARY_PATH:+:${LIBRARY_PATH}}

# Upgrade the image with the latest patches

RUN apt-get update \
 && apt-get upgrade --yes \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*
