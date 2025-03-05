# Installing Python 2.7 and pip on Ubuntu 24.04 Noble LTS

Ubuntu 24.04 does not include Python 2.7 by default, as it has reached its end of life. However, if you need it for legacy applications, you can install it by compiling from source.

## Installing Python 2.7

1. **Update the system packages:**
    ```bash
    sudo apt update && sudo apt upgrade
    ```
2. **Install required dependencies:**
    ```bash
    sudo apt install -y build-essential checkinstall libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev
    ```
3. **Download Python 2.7.18 source code:**
    ```bash
    cd /usr/src
    wget https://www.python.org/ftp/python/2.7.18/Python-2.7.18.tgz
    ```
4. **Extract the downloaded file:**
    ```bash
    tar xzf Python-2.7.18.tgz
    cd Python-2.7.18
    ```
5. **Configure and compile Python 2.7:**
    ```bash
    ./configure --enable-optimizations
    make
    sudo make install
    ```

6. **Verify installation:**
    ```bash
    python -V
    ```
    Expected output:
    ```
    Python 2.7.18
    ```

## Installing `pip` for Python 2.7

1. **Install `curl` if not installed:**
    ```bash
    sudo apt install curl
    ```
2. **Download the `get-pip.py` script:**
    ```bash
    curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
    ```
3. **Run the script using Python 2.7:**
    ```bash
    sudo python2.7 get-pip.py
    ```
4. **Verify pip installation:**
    ```bash
    pip2.7 --version
    ```

## Disclaimer
Python 2 is deprecated and no longer maintained. It is recommended to transition to Python 3 for ongoing support and security updates.

## References
- [Original Guide](https://linux.how2shout.com/how-to-install-python-2-7-on-ubuntu-24-04-noble-lts-linux/)

