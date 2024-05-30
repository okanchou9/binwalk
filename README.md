# Binwalk


新版 binwalk 虽然解决了依赖问题，但是新引入bug，导致某些固件无法解压，这点在 Ubuntu 22.04 以及 Kali Linux 2023 以上版本表现尤为明显。

```shell
git clone https://github.com/liyansong2018/binwalk.git
cd binwalk
./dep.sh
sudo python3 setup.py install
```

本次修复内容如下

- 删除过时的 `python2` 和一系列无法安装的 `python2` 依赖包
- 增加 `cramfsprogs` 的正确安装
- 合入 `sasquatch` 针对 `gcc 10` 以上版本的补丁，该补丁已提交`binwalk`原作者的项目
- 增加 `pip` 代理的国内源，大幅提高依赖下载速度
- 更新`ubireader`

修改后的 binwalk 可支持原本 binwalk 不支持的固件，例如

- DIR-300A1_FW105b09.bin（新版 binwalk 引入的新 Bug，导致无法解压）
- Archer C5400X_V1_240510.zip（过时的 ubireader 导致的 binwalk 无法解压 ）