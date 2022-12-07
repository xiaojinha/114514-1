# 使用Github Action行动来编译恢复

- 支持 ~~OFRP~~, SHRP, TWRP 的编译和生产

---

## 感谢
- 所有贡献者

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
For example, your username is: JohnSmith
```
#### 1. Click 'Fork' in the upper right corner of this repository
![image](https://user-images.githubusercontent.com/37921907/177914706-c92476c5-7e14-4fb3-be94-0c8a11dae874.png)
#### 2. After waiting for the automatic redirection, you will see your own username
![image](https://user-images.githubusercontent.com/37921907/177915106-5bde6fc9-303c-479e-b290-22b48efd1e4e.png)
#### 3. Change the [username and email](https://github.com/CaptainThrowback/Action-Recovery-Builder/blob/main/.github/workflows/Recovery%20Build.yml#L100-L101) in the workflow to reflect your Github credentials (optional)
## Setting up SSH Keys (optional)
#### 4. Go to Settings, then select Deploy keys and select "Add deploy key" button.

#### 5. On your Android device, install [Termux](https://github.com/termux/termux-app/releases)

#### 6. Install openssh in Termux and generate ssh keys. (Do not use passphrase for keys)
NOTE: When creating the deploy key for a repository like git@github.com:owner/repo.git or https://github.com/owner/repo, put that URL into the key comment. (Hint: Try ssh-keygen ... -C "git@github.com:owner/repo.git".)
owner = your Github username
```
pkg install openssh
ssh-keygen -t ed25519 -C "git@github.com:owner/Action-Recovery-Builder.git"
```
#### 7. Add the keys to your repo. In Termux, use the following commands:
```
cd /data/data/com.termux/files/usr/etc/ssh
cat ssh_host_ed25519_key.pub
```
  Select and copy the key then paste in the box for Key.
  You can name it whatever you choose for the title.

#### 8. Now to add your private ssh key. Back in Termux:
```
cat ssh_host_ed25519_key
```
   Copy the output from Termux.

   In your browser, select *Secrets* under the Security tab.
   Select Actions
   Select New repository secret
   For the New secret name, it should be SSH_PRIVATE_KEY
   Paste the output from ssh_host_ed25519_key into the Value box.
   Then select Add secret.

## Building the Recovery
#### 9. Click 'Actions-Recovery Build'
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
