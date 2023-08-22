# 网络RTK基站配置给GRTK Rover使用实现RTK定位

!!! warning "网络RTK基站具有覆盖范围大，不受基站位置限制的优势，但由于基站距离移动站距离通常较远，而GRTK的水位定位精度为 0.8cm+1ppm，即基站与移动站距离每超过10Km，定位精度将下降1cm，因而出现定位精度下降的情况是预期中的，实际定位精度需综合网络基站服务提供商和网络状态等因素。"

## 网络RTK基站服务的选择

!!! info 
    - 网络RTK基站服务通常遵从`Ntrip`协议, 购买服务请与服务提供商确认
    - `端口`请选择 **WGS84坐标系**
    - `源节点`请选择**五星十六频**

## CORS账号示例

!!! info "账号信息"
    网络RTK服务账号至少应包含：

    - 账号
    - 密码
    - IP
    - 端口（port）
    - 源节点（mount）

```
账号:cedr5668 密码:km1y27vr

cors账号配置方法：
移动CORS设置方式：
①IP：120.253.239.161
②端口：8001对应CGCS2000坐标系，8002端口对应WGS84坐标系，记得中央子午线改成当地
③源节点：
RTCM33_GRCEJ（五星十六频，推荐五星仪器以上使用）
RTCM33_GRCEpro（四星十三频，推荐四星仪器以上使用）
RTCM33_GRCE（四星十一频，推荐四星仪器以上使用）
RTCM33_GRC（三星八频，推荐三星仪器使用）
RTCM30_GR（双星仪器使用）
```

## 使用Mission Planner转发网络基站RTCM数据给Rover

!!! info "要首先通过数传将Pixhawk与Mission Planner连接上"

### RTK/GPS Inject

!!! info "初始设置 -> RTK/GPS Inject -> Ntrip -> Connect"

![](../media/mp-ntrip-1.png){ width="500" }

### 输入Ntrip账号信息

!!! info "以CORS账号服务为例"
    http://cedr5668:km1y27vr@120.253.239.161:8002/RTCM33_GRCEJ

![](../media/mp-ntrip-2.png){ width="500" }

### 连接成功

![](../media/mp-ntrip-3.png){ width="500" }

!!! info "GPS 显示为 RTK Float"
    进入rtk定位，但此时GRTK的`RTK`灯并不会亮

![](../media/mp-ntrip-4.png){ width="500" }


!!! info "GPS 显示为 RTK Fixed"
    进入高精rtk定位，此时GRTK的`RTK`灯亮起
    具体进入RTK Fixed的时间主要取决于网络RTK数据

![](../media/mp-ntrip-5.png){ width="500" }

## 使用RTK lib转发网络基站RTCM数据给Rover

!!! info "使用RTK lib中的 strsvr.exe"

### 配置Ntrip服务

!!! info "Input"
    选择 `NTRIP Client` 
    配置按照CORS账号进行填写

![](../media/rtk-ntrip-1.png){ width="500" }

!!! info "Output"
    选择 `Serial` 
    配置按照转发给`GRTK Rover`的数传串口进行配置

![](../media/rtk-ntrip-2.png){ width="500" }

!!! info "Options"
    勾选 `NMEA Cycle` 并设置为 1000
    `Lat/Lon/Height` 按照GRTK Rover实际坐标进行填写

![](../media/rtk-ntrip-3.png){ width="500" }

### 开始转发

!!! info "点击Start"
    成功配置后可以看到Bytes值增加很快
    如果只有2Byte 说明没有配置成功，请重新检查配置

![](../media/rtk-ntrip-4.png){ width="500" }

### 观测Rover定位数据

!!! info "未转发网络基站数据时定位状态只有**DGPS**"
    位置飘动在米级

![](../media/rtk-ntrip-5.png){ width="500" }

!!! info "刚开始转发网络基站数据时定位状态变为**FLOAT**"
    位置飘动在分米级

![](../media/rtk-ntrip-6.png){ width="500" }

!!! info "大约1分钟后（具体视当前收星和服务提供商状态）定位状态变为**FLOAT**"
    位置趋于稳定，飘动为厘米级

![](../media/rtk-ntrip-7.png){ width="500" }
![](../media/rtk-ntrip-8.png){ width="500" }