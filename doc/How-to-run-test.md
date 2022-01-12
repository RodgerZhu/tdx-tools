## TDX Test

The TDX test suite package ships a python virtual environment containing the required
modules to run the tests. Assuming you are using CentOS Stream, they can be verified and installed if needed by running:

```
sudo dnf install python3-libvirt-6.0.0 python3-libguestfs libguestfs-devel libvirt-devel python3-devel
```

With dependency packages installed, it is ready for the next steps:

1. Clone the TDX test suite:

    ```
    git clone git@github.com:intel/tdx-test.git
    ```

2. Create an virtual environment and required library:

    ```
    source setupenv.sh
    ```

    _NOTE:_

    - All dependent packages will be downloaded and installed into `<this_repo_dir>/venv`
    - If it fails to download the python PIP packages from official PIP server due to proxy issue,
      please try the PIP mirror servers. For example using PRC `tsinghua` university,
      create a new file ~/.pip/pip.conf with following contents:

    ```
    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
    ```

3. Use `run.sh` to select the bat test suite:

    ```
    ./run.sh -s bat
    ```

*NOTES*:

- if running as a regular user, `sudo` may be necessary to run some test cases
- regular users must be part of libvirt group. That can be done using `sudo usermod -aG libvirt $USER`
