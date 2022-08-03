# Docker-Python_sample
## building Python environment by Docker
以下のコマンドをDockerfileのあるディレクトリで実行する  
> docker compose up -d  
> docker exec -it con_python3 bash

- ベースはDockerhubにあるPython Image
- requirements.txtに記載のパッケージがbuild時にインストールされる
- ./src/がコンテナ内の/root/src/にマウントされる
    - マウントするディレクトリはdocker-compose.ymlのservices:python3:volumesから編集可能
        - (マウントするpath):(マウント先の(コンテナ内の)path)

- git commit等はコンテナの外から行う
    - コンテナにはターミナルから接続し、VSCodeではコンテナの外からgit操作等を行う
        - ./srcを/root/src/にマウントしているので、コンテナの外から/root/src/内のファイルを編集できる

- VSCodeのDocker拡張から、稼働中のコンテナを右クリック→Attach Visual Studio Codeすると、コンテナの中からコードの編集等を行うこともできる
    - Pythonインタプリタに依存したVSCodeの機能を使いたいときなどはこうしたほうがいい？

- .bashrcはコンテナ内bashの見た目をいじるファイル
    - お好みで変えてください
