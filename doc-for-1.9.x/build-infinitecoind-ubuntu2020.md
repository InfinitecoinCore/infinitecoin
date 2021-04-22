//编译无界面钱包

sudo apt-get update

//libminiupnpc-dev ifc编译可以不安装
sudo apt-get install libminiupnpc-dev

//安装基本环境
sudo apt-get install -y make gcc g++ git libssl-dev build-essential libtool autotools-dev autoconf pkg-config libevent-dev libboost-all-dev libboost-dev libboost-system-dev libboost-filesystem-dev libboost-program-options-dev libboost-thread-dev libqrencode-dev libpng-dev

sudo apt-get install -y libfontconfig1-dev libfreetype6-dev libx11-dev libxcursor-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxrandr-dev libxrender-dev


sudo apt-get install unzip && wget http://download.oracle.com/berkeley-db/db-4.8.30.zip && unzip db-4.8.30.zip && sed -i 's/__atomic_compare_exchange/__atomic_compare_exchange_db/g' db-4.8.30/dbinc/atomic.h && cd db-4.8.30 && cd build_unix/ && ../dist/configure --prefix=/usr/local --enable-cxx && make && make install && cd ~

wget 'http://fukuchi.org/works/qrencode/qrencode-3.2.0.tar.bz2' --no-check-certificate && tar xjf qrencode-3.2.0.tar.bz2 && cd qrencode-3.2.0 && ./configure --enable-static --disable-shared && make install && cd ~

//下载源码
cd ~ && mkdir ifc && cd ifc && git clone https://github.com/InfinitecoinCore/infinitecoin.git

//编译无界面钱包 infinitecoind
cd ~/ifc/infinitecoin/src/ && make -f makefile.unix STATIC=1 USE_UPNP=- USE_IPV6=0 && strip infinitecoind