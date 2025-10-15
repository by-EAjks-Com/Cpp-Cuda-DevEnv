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

# Add the Intel/OneAPI packages

RUN apt-get update \
 && apt-get install --yes --no-install-recommends \
        git=1:2.51.0-1ubuntu1 \
        git-flow=1.12.3-3 \
        cmake=3.31.6-2ubuntu6 \
        ninja-build=1.12.1-1 \
        ccache=4.11.2-2 \
        build-essential=12.12ubuntu1 \
        llvm=1:20.0-63ubuntu1 \
        clang=1:20.0-63ubuntu1 \
        clang-format=1:20.0-63ubuntu1 \
        clang-tidy=1:20.0-63ubuntu1 \
        clang-tools=1:20.0-63ubuntu1 \
        lld=1:20.0-63ubuntu1 \
        llvm-20=1:20.1.8-0ubuntu4 \
        clang-20=1:20.1.8-0ubuntu4 \
        clang-format-20=1:20.1.8-0ubuntu4 \
        clang-tidy-20=1:20.1.8-0ubuntu4 \
        clang-tools-20=1:20.1.8-0ubuntu4 \
        lld-20=1:20.1.8-0ubuntu4 \
        llvm-21=1:21.1.2-2ubuntu6 \
        clang-21=1:21.1.2-2ubuntu6 \
        clang-format-21=1:21.1.2-2ubuntu6 \
        clang-tidy-21=1:21.1.2-2ubuntu6 \
        clang-tools-21=1:21.1.2-2ubuntu6 \
        lld-21=1:21.1.2-2ubuntu6 \
        doxygen=1.9.8+ds-2.1build1 \
        doxygen-latex=1.9.8+ds-2.1build1 \
        graphviz=2.42.4-3build2 \
        intel-oneapi-common-licensing-2025.2=2025.2.0-377 \
        intel-oneapi-dpcpp-cpp-2025.2=2025.2.1-7 \
        libssl-dev=3.5.3-1ubuntu2 \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*

RUN apt-mark hold \
        git \
        git-flow \
        cmake \
        ninja-build \
        ccache \
        build-essential \
        llvm \
        clang \
        clang-format \
        clang-tidy \
        clang-tools \
        lld \
        llvm-20 \
        clang-20 \
        clang-format-20 \
        clang-tidy-20 \
        clang-tools-20 \
        lld-20 \
        llvm-21 \
        clang-21 \
        clang-format-21 \
        clang-tidy-21 \
        clang-tools-21 \
        lld-21 \
        doxygen \
        doxygen-latex \
        graphviz \
        intel-oneapi-common-licensing-2025.2 \
        intel-oneapi-dpcpp-cpp-2025.2 \
        libssl-dev

# Add Nvidia CUDA support

RUN apt-get update \
 && apt-get install --yes --no-install-recommends \
        cuda-cudart-dev-13-0=13.0.96-1 \
        cuda-command-line-tools-13-0=13.0.2-1 \
        cuda-minimal-build-13-0=13.0.2-1 \
        cuda-libraries-dev-13-0=13.0.2-1 \
        cuda-nvml-dev-13-0=13.0.87-1 \
        libnpp-dev-13-0=13.0.1.2-1 \
        libcublas-dev-13-0=13.1.0.3-1 \
        libcusparse-dev-13-0=12.6.3.3-1 \
        libnccl-dev=2.28.3-1+cuda13.0 \
        cuda-nsight-compute-13-0=13.0.2-1 \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*

RUN apt-mark hold \
        cuda-cudart-dev-13-0 \
        cuda-command-line-tools-13-0 \
        cuda-minimal-build-13-0 \
        cuda-libraries-dev-13-0 \
        cuda-nvml-dev-13-0 \
        libnpp-dev-13-0 \
        libcublas-dev-13-0 \
        libcusparse-dev-13-0 \
        libnccl-dev \
        cuda-nsight-compute-13-0

ENV LIBRARY_PATH=/usr/local/cuda/lib64/stubs${LIBRARY_PATH:+:${LIBRARY_PATH}}

# Upgrade the image with the latest patches

RUN apt-get update \
 && apt-get upgrade --yes \
 && apt-get autoremove --yes --purge \
 && rm -rf /var/lib/apt/lists/*
