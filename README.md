# 使用Github Action来编译恢复

- 支持 ~~OFRP~~, SHRP, TWRP 的编译和生产

---

## 感谢
- 所有贡献者
- 莫莫汉化

---

## 发布说明
```
= 2022/10/28
- OFRP清单已被修改，所以现在不完全支持OFRP（如果你能解决这个问题，请提交一个拉动请求！）。

= 2022/07/08
- TWRP和基于TWRP的5.X ~ 12.X是***全部成功编译的***。

= 2022/07/06
- Add support for 5.1 branch

= 2022/07/05
- Updated to work with trees back to 6.0
- Add conditionals to include common trees for syncing
- Update README for SSH keys

= 2022/07/04
- Updated to work with Android 12.1 AOSP minimal TWRP manifest

= 2022/05/29
- Should work correctly with Android 11 based source code

= 2022/02/03
- Due to the hardware resource limitation of GitHub action, this version cannot be compiled based on AOSP and other source codes of Android 11 and above. If necessary, please use local compilation

= 2021/10/29: 
- Refactored version 2.0
- Completely reconstruct the use logic to reduce the difficulty of use
- Optimize the parameter transfer part, now you can run multiple Workers at the same time
```

-----

## 参数描述

| 名称 | 描述 | 示例 |
| ------------ | -------------------- | ------------ |
| `MANIFEST_URL` | 源码地址 | https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git |
| `MANIFEST_BRANCH` | 源码分支 | twrp-12.1 |
| `DEVICE_TREE_URL` | 设备树地址 | https://github.com/TeamWin/android_device_asus_I003D |
| `DEVICE_TREE_BRANCH` | 设备树分支 | android-12.1 |
| `DEVICE_PATH` | Device location | device/asus/I003D |
| `COMMON_TREE_URL` | 设备位置 | https://github.com/TeamWin/android_device_asus_sm8250-common |
| `COMMON_PATH` | 通用设备树地址 | device/asus/sm8250-common |
| `DEVICE_NAME` | 机型名称 | I003D |
| `MAKEFILE_NAME` | 编译文件名 | omni_I003D |
| `BUILD_TARGET` | 建立目标分区 (boot/recovery/vendorboot) | recovery |

-----

## 怎样使用？
```
例如，你的用户名是：JohnSmith
```
#### 1. 点击该资源库右上角的'Fork'
![image](https://user-images.githubusercontent.com/37921907/177914706-c92476c5-7e14-4fb3-be94-0c8a11dae874.png)
#### 2. 在等待自动重定向后，你会看到你自己的用户名
![image](https://user-images.githubusercontent.com/37921907/177915106-5bde6fc9-303c-479e-b290-22b48efd1e4e.png)
#### 3. 改变[用户名和电子邮件](https://github.com/CaptainThrowback/Action-Recovery-Builder/blob/main/.github/workflows/Recovery%20Build.yml#L100-L101) 在工作流程中反映你的Github证书（可选）
## 设置SSH密钥（可选）
#### 4. 进入设置，然后选择部署密钥，选择 "添加部署密钥 "按钮。

#### 5. 在你的安卓设备上，安装[Termux](https://github.com/termux/termux-app/releases)

#### 6. 在Termux中安装openssh并生成ssh密钥。(不要使用密钥的口令)
NOTE: When creating the deploy key for a repository like git@github.com:owner/repo.git or https://github.com/owner/repo, put that URL into the key comment. (Hint: Try ssh-keygen ... -C "git@github.com:owner/repo.git".)
owner = your Github username
```
pkg install openssh
ssh-keygen -t ed25519 -C "git@github.com:owner/Action-Recovery-Builder.git"
```
#### 7. 将密钥添加到你的 repo 中。在Termux中，使用以下命令。
```
cd /data/data/com.termux/files/usr/etc/ssh
cat ssh_host_ed25519_key.pub
```
  Select and copy the key then paste in the box for Key.
  You can name it whatever you choose for the title.

#### 8. 现在要添加你的私人SSH密钥。回到Termux中。
```
cat ssh_host_ed25519_key
```
   复制Termux的输出。

   在你的浏览器中，选择安全标签下的*秘密*。
   选择 Actions
   选择 New repository secret
   对于新的秘密名称，它应该是 SSH_PRIVATE_KEY
   将ssh_host_ed25519_key的输出粘贴到Value框中。
   然后选择 Add secret.

## 构建恢复
#### 9. 点击 'Actions-Recovery Build'
![image](https://user-images.githubusercontent.com/37921907/177915304-8731ed80-1d49-48c9-9848-70d0ac8f2720.png)
#### 10. Click 'Run workflow' and fill in according to the above 'parameter description'
![image](https://user-images.githubusercontent.com/37921907/177915346-71c29149-78fb-4a00-996f-5d84ffc9eb8c.png)
#### 11. After filling in, click 'Run workflow' to start running

-----

## Compilation results
Can be downloaded at [Release](../../releases)

-----
## Remark

#### TeamWin Recovery Project: https://github.com/minimal-manifest-twrp
#### OrangeFox Recovery Project: https://gitlab.com/OrangeFox/Manifest
#### SKYHAWK Recovery Project: https://github.com/SHRP/platform_manifest_twrp_omni
