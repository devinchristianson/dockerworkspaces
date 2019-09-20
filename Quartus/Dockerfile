FROM centos:7

# Set LOCALE to UTF8
#RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
#    locale-gen en_US.UTF-8 && \
#    /usr/sbin/update-locale LANG=en_US.UTF-8

# adding scripts
ADD files/setup /root/
ADD files/.profile /root/
ADD files/usr/local/bin/quartus_wrapper /usr/local/bin/quartus_wrapper

RUN echo "QT_X11_NO_MITSHM=1" >> /etc/environment

# install quartus prime
ADD ./QPkg /root/quartus

# basic packackages
RUN echo "multilib_policy=all" >> /etc/yum.conf
RUN yum install -y yum-plugin-fastestmirror epel-release

RUN yum update -y && yum install -y tcsh expect xorg-x11-server-Xorg \
    unixODBC-devel unixODBC ncurses ncurses-libs zeromq3 libXext alsa-lib \
    libXtst libXft libxml2 libedit libX11 libXi libpng12 libSM expat fontconfig \
    freetype glibc gtk2 libcanberra libICE libpng libSM libX11 libXau libXdmcp \
    libXext libXft libXrender libXt libXtst ncurses ncurses-devel util-linux zlib \
    libpng12 patchelf

RUN  cd /root/quartus && \ 
    /root/setup && rm -rf /root/quartus && rm -rf /root/setup
ENV PATH="/opt/intelFPGA_lite/18.1/quartus/sopc_builder/bin/:/opt/intelFPGA_lite/18.1/quartus/bin/:${PATH}"
CMD ["quartus"]
