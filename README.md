# ms_a010_test
[![Open in Dev Containers](https://img.shields.io/static/v1?label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/teruyamato0731/ms_a010_test)

ms a010のdev container開発環境。
X11をマウントしてGUIアプリの使用ができるようにしている。
Ubuntu 22.04で動作確認済み。

# Quick Start
あなたがすでにVS CodeとDockerをインストールしている場合は、上記のバッジまたは[こちら](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/teruyamato0731/ms_a010_test)をクリックすることで使用することができる。<br>
これらのリンクをクリックすると、vscodeが必要に応じてdev container拡張機能を自動的にインストールし、ソースコードをコンテナボリュームにクローンし、使用するためのdev containerを起動する。

# How to use
1. Docker, vscode, devcontainer拡張機能をインストールする。
1. X11のアクセスをローカルに対して許可する。
    ```bash
    xhost +local:
    # non-network local connections being added to access control list
    ```
1. リポジトリをcloneしvscodeで開く。
    ```bash
    git clone https://github.com/teruyamato0731/ms_a010_test.git
    code ms_a010_test
    ```
1. 「Reopen in Container」でdevcontainerを開く
1. ```bash
    sudo apt update && rosdep update && rosdep install --from-path src --ignore-src -y
    colcon build
    source install/local_setup.bash
    sudo adduser $USER dialout
    ros2 run sipeed_tof_ms_a010 publisher --ros-args -p device:="/dev/ttyUSB0"
    ```
    ```bash
    ```

# reference
https://dl.sipeed.com/shareURL/MaixSense/MaixSense_A010/software_pack/SDK
https://blog.mmaakkyyii.com/posts/post42/
