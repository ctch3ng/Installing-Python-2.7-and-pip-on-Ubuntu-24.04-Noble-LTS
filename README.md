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
    When configuring the build, you have two options for the compilation:
    
    Option 1: Standard Build (Recommended for simplicity)
    This option compiles Python without advanced optimizations, resulting in a cleaner and faster build process. By using `--prefix=/usr/local/python2.7`, you ensure the Python 2.7 executable is         installed as `/usr/local/python2.7/bin/python`. This can avoid overwriting or conflicting with files belonging to the system's default Python 3 installation, potentially breaking system utilities that rely on Python 3.
    
    ```bash
    ./configure --prefix=/usr/local/python2.7
    make
    sudo make install
    ```
    
    Option 2: Optimized Build (For potential performance gains)
    The `--enable-optimizations` flag enables Profile-Guided Optimization (PGO), which can result in a slightly faster interpreter. 
    Note: This could increase the compile time and will produce a large amount of verbose output, including warnings/logs, during the make step. 
    
    ```bash
    ./configure --enable-optimizations --prefix=/usr/local/python2.7
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

