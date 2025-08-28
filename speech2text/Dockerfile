# Copyright (c) 2025 Intel Corporation
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ============================================================================

FROM quay.io/redhat-user-workloads/octo-edge-tenant/jetson-wheels-vllm-app:latest

USER root

RUN uv pip install openai-whisper

WORKDIR /workspace
COPY ./ /workspace/

# mlperf loadgen
RUN dnf install -y git-core
RUN mkdir -p /workspace/third_party && cd /workspace/third_party && \
    git clone https://github.com/mlcommons/inference.git mlperf-inference && cd mlperf-inference && git checkout 2814499 && cd loadgen && \
    uv pip install . && \
    cp /workspace/third_party/mlperf-inference/mlperf.conf /workspace/
