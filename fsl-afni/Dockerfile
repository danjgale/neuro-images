FROM fsl

# Install AFNI
ENV PATH="/opt/afni-latest:$PATH" \
    AFNI_PLUGINPATH="/opt/afni-latest"
RUN apt-get update -qq \
    && apt-get install -y -q --no-install-recommends \
           ca-certificates \
           cmake \
           curl \
           ed \
           gsl-bin \
           libcurl4-openssl-dev \
           libgl1-mesa-dri \
           libglib2.0-0 \
           libglu1-mesa-dev \
           libglw1-mesa \
           libgomp1 \
           libjpeg62-turbo-dev \
           libjpeg62 \
           libssl-dev \
           libudunits2-dev \
           libxm4 \
           multiarch-support \
           netpbm \
           python3-pip \
           tcsh \
           xfonts-base \
           xvfb \
    && rm -rf /var/lib/apt/lists/* \
    && _reproenv_tmppath="$(mktemp -t tmp.XXXXXXXXXX.deb)" \
    && curl -fsSL --retry 5 -o "${_reproenv_tmppath}" http://mirrors.kernel.org/debian/pool/main/libx/libxp/libxp6_1.0.2-2_amd64.deb \
    && apt-get install --yes -q "${_reproenv_tmppath}" \
    && rm "${_reproenv_tmppath}" \
    && _reproenv_tmppath="$(mktemp -t tmp.XXXXXXXXXX.deb)" \
    && curl -fsSL --retry 5 -o "${_reproenv_tmppath}" http://snapshot.debian.org/archive/debian-security/20160113T213056Z/pool/updates/main/libp/libpng/libpng12-0_1.2.49-1%2Bdeb7u2_amd64.deb \
    && apt-get install --yes -q "${_reproenv_tmppath}" \
    && rm "${_reproenv_tmppath}" \
    && apt-get update -qq \
    && apt-get install --yes --quiet --fix-missing \
    && rm -rf /var/lib/apt/lists/* \
    && gsl_path="$(find / -name 'libgsl.so.??' || printf '')" \
    && if [ -n "$gsl_path" ]; then \
         ln -sfv "$gsl_path" "$(dirname $gsl_path)/libgsl.so.0"; \
    fi \
    && ldconfig \
    && mkdir -p /opt/afni-latest \
    && echo "Downloading AFNI ..." \
    && curl -fL https://afni.nimh.nih.gov/pub/dist/tgz/linux_openmp_64.tgz \
    | tar -xz -C /opt/afni-latest --strip-components 1
