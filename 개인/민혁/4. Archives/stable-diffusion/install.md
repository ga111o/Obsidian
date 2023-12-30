git clone

1. apt update
    ```
    sudo apt-get update
    sudo apt install -y ubuntu-drivers-common
    ```

---

2. move dir, git clone
    ```
    mkdir {folder-name}
    cd {folder-name}
    git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
    ```

---

3. install

    ```
    cd stable-diffusion-webui/
    ./webui.sh --xformers

    #if no gpu(cuda)
    ./webui.sh --xformers --skip-torch-cuda-test
    ```

---

recommend work on windows