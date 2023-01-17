# On ARM Architecture
sudo cp /etc/apt/sources.list /etc/apt/sources.list~
sudo sed -Ei 's/^# deb-src /deb-src /' /etc/apt/sources.list
sudo apt update
sudo apt-get build-dep r-base

sudo apt-get install build-essential
sudo apt-get install gfortran
sudo apt-get install libxml2-dev
sudo apt-get install libssl-dev

export R_VERSION=4.2.2
curl -O https://cran.rstudio.com/src/base/R-4/R-${R_VERSION}.tar.gz
tar -xzvf R-${R_VERSION}.tar.gz
cd R-${R_VERSION}
./configure \
    --prefix=/opt/R/${R_VERSION} \
    --enable-memory-profiling \
    --enable-R-shlib \
    --with-blas \
    --with-lapack \
    --with-x=no

make
sudo make install

/opt/R/${R_VERSION}/bin/R --version

sudo ln -s /opt/R/${R_VERSION}/bin/R /usr/local/bin/R
sudo ln -s /opt/R/${R_VERSION}/bin/Rscript /usr/local/bin/Rscript

#sudo chmod -R go+w /opt/R/4.2.2/lib/R/library
#sudo chmod -R go+w /opt/R/4.2.2/lib/R/doc

sudo vi /etc/environment
>R_LIBS_USER=~/.local/lib/R/site-library

# On intel x64 architecture
