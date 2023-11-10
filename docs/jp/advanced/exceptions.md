---
headerDepth: 2
icon: iconfont icon-warn
category: [FAQ]
order: 2
redirectFrom: /en/advanced/mihoyo-risk-tip.html
comment: false
---

# 一般的なプログラム例外

このドキュメントでは、 **予見可能なクライアント エラー** の解決策について説明します。

## RuntimeEnvironmentException

- Exception: `RuntimeEnvironmentException`
  - Hint: `Unable to set registry key without enabling long path`
- Issue source: Windows long path limit is set to be limited at 256 characters by default
- Solution: Download [EnableLongPaths.zip](https://d.hut.ao/d/tools/EnableLongPaths.zip), unzip it and run `.reg` file

## Return Code: -10001

- This error comes directly from MiHoYo BBS, hints include
  - `Return Code: -10001`
  - `Return Code: -100`
- Issue source
  1. Cookie expired
  2. Network error
  3. System time is not accurate
- Solution
  1. In the account panel, execute `Refresh Cookies`
  2. Remove your account and add it again
  3. Sync your system time

## Return Code: 1034 Verification Failed

- If Snap Hutao returns `1034` status code and hints verification failed (usually during the operation of Realtime Notes),
  it means the operation is blocked by MiHoYo BBS anti-bot system
- Solution:
  - Enter `Realtime Notes`
  - Click on `Verify Current User and Role` button
  - Follow the instruction in MiHoYo BBS to verify
  - After finishing the verification process, click `Complete` to close the verification window
  - Now, the account should back to normal; If not, process the step above again
    ::: tip

If the risk prompt is too frequent, or the verification cannot be triggered at all, it means that the risk of your
account is too high, please change the password, so that the simultaneous login status of multiple devices will be reset

:::

::: warning

- You hardly cannot pass imperceptible verification when your account is **login at other remote Genshin tools** or
  **login at multiple devices**. This is a security designing of MiHoYo BBS, and cannot bypass
- If you are using **multiple MiHoYo BBS account in your device**, **frequent usage with MiHoYo BBS API** will
  result in your IP address being banned for a period of time (usually no more than 24 hours). This is a security
  designing of MiHoYo BBS, and cannot bypass

:::

## HttpRequestException Metadata Download Failed

### 403 (Forbidden) / 404 (Not Found)

Solution: Update your Snap Hutao to latest version

### 502 (Bad Gateway)

> Associated Issue: [https://github.com/DGP-Studio/Snap.Hutao/issues/100](https://github.com/DGP-Studio/Snap.Hutao/issues/100)

This HTTP Exception occurs when Snap Hutao failed to fetch remote resource (usually static image and configuration)

![HttpRequestException](https://img.alicdn.com/imgextra/i3/1797064093/O1CN01Tb2RUm1g6du5YeNuy_!!1797064093.jpg)

If you are using proxy software, you may need to turn it off or using TUN mode proxy;
otherwise you need to use [Windows 8 AppContainer Loopback Utility](https://www.telerik.com/fiddler/add-ons) to remove
[Windows APP Container Loopback limits](https://learn.microsoft.com/zh-CN/windows/iot-core/develop-your-app/loopback).

You can also execute the following PowerShell script to remove all container loopback limits

```powershell
FOR /F "tokens=11 delims=\" %p IN ('REG QUERY "HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\Mappings"') DO CheckNetIsolation.exe LoopbackExempt -a -p=%p
```

## Error Finding Required Modules

When user launching game with unlock frame-rate feature on, the game may be failed to be launched with the following error shows up:

1. Error finding required modules: could not read any module, the protection driver may have been loaded
2. Error finding required modules: timeout

This issue only occurs when Genshin Impact's anti-cheat module starts earlier than frame-rate-unlocker module.
When these errors happen, Snap Hutao will exit game process, and you can re-launch the game.
