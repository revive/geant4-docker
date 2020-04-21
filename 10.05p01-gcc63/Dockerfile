FROM debian:stretch-slim

# download geant4 src

WORKDIR /tmp

RUN apt-get update && apt-get install -y g++ cmake curl qtbase5-dev libxerces-c-dev libexpat1-dev
RUN mkdir -p /usr/src/geant4-src \
        &&     curl -SL http://geant4-data.web.cern.ch/geant4-data/releases/geant4.10.05.p01.tar.gz\
        | tar zx --strip-component=1 -C /usr/src/geant4-src \
        &&  mkdir geant4-build && cd geant4-build \
        && cmake -DGEANT4_USE_QT=ON -DGEANT4_USE_GDML=ON -DGEANT4_INSTALL_DATA=OFF /usr/src/geant4-src && make && make install

RUN rm -rf *

RUN rm -rf /usr/src/geant4-src

ENTRYPOINT ["/bin/bash"]
