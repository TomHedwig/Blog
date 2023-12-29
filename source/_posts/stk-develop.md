---
title: STK 二次开发的注意事项
date: 2023-12-26 11:45:42
categories:
    - 编程
tags:
    - STK
    - C#
description: 本文列举了一些在使用C#进行STK二次开发时的操作及应注意的事项
---

+ 新建项目前，对 STK 9 和 STK 11，均以管理员权限运行 *STK Install Folder \ bin \ AgPluginReg.exe* 以注册所有 *.dll* 文件

    ![](https://hxyx-blog-resource.vercel.app/img/stk_Register.bmp)

+ 新建项目时，注意 STK 9 和 STK 11 均只支持 .net Framework 而不支持 .net Core

+ 在项目属性（Properties）中，对于构建（Build）中的目标平台（Platform target）设置，STK 9 和 STK 11 有所区别：

    + STK 9 应选择 **x86**

      ![](https://hxyx-blog-resource.vercel.app/img/stk9_Build.bmp)

    + STK 11 应选择 **any CPU** 并保持 **Prefer 32-bit** 选项处于未勾选的状态

      ![](https://hxyx-blog-resource.vercel.app/img/stk11_Build.bmp)

      

+ 设置项目引用时，STK 9 和 STK 11 均需要在 *Reference Manager > Assemblies > Framework* 中勾选以下内容：

    + **System.Drawing**

    + **System.Windows.Forms**

    + **WindowsFormsIntegration**

      ![](https://hxyx-blog-resource.vercel.app/img/stk_Assembly_1.bmp)

      ![](https://hxyx-blog-resource.vercel.app/img/stk_Assembly_2.bmp)

+ 在 COM 引用的设置中，STK 9 与 STK 11 有所区别：

    + STK 9 应在 *Peference Manager > COM > Type Libraries* 中勾选以下选项：

        + **AGI STK Objects 9**

        + **AGI STK Util 9**

        + **AGI STK VGT 9**

        + **AGI STK X 9**

          ![](https://hxyx-blog-resource.vercel.app/img/stk9_COM_1.bmp)

        并在 *Peference Manager > Browse* 中打开 *STK 9 Install Folder \ bin \ Primary Interop Assemblies* 以添加以下文件：

        + **AGI.STKX.Interop.dll**

        + **AxAGI.STKX.Interop.dll**

          ![](https://hxyx-blog-resource.vercel.app/img/stk9_COM_2.bmp)

    + STK 11 应在 *Peference Manager > Browse* 中打开 *STK 11 Install Folder \ bin \ Primary Interop Assemblies* 以添加以下文件：

        + **AGI.STKX.Controls.Interop.dll**

        + **AGI.STKXGraphics.Interop.dll**

        + **AGI.STKUtil.Interop.dll**

        + **AGI.STKX.Interop.dll**

        + **AGI.STKVgt.Interop.dll**

        + **AGI.STKObjects.Interop.dll**
        
          ![](https://hxyx-blog-resource.vercel.app/img/stk11_COM.bmp)

+ 完成后，必须将上述引用的 **全部内容** 的 **Embed Interop Types** 属性设置为 **false**

    ![](https://hxyx-blog-resource.vercel.app/img/stk_Properties.bmp)

+ 在创建 *AgStkObjectRoot* 的新实例时，需要注意的是，若当前程序中不存在以下内容中的任意一个：
  
    + *AxAgUiAxVOCntrl* 控件

    + *AxAgUiAx2DCntrl* 控件

    + *AgSTKXApplication* 实例
    
    则会抛出异常：

    System.Runtime.InteropServices.COMException: 'Creating an instance of the COM component with CLSID {CBC2BA60-DA3D-43BD-A068-C6F03149931D} from the IClassFactory failed due to the following error: 80040204 An invalid field name was used in a query string (Exception from HRESULT: 0x80040204).'

    因此，最好在程序的开始创建一个 *AgSTKXApplication* 实例以避免抛出异常，即：

    ```c#
    AgSTKXApplication stk_instance = new AgSTKXApplication();
    ```

+ 以下是一些 AGI 官方提供的帮助文档：

    + https://help.agi.com/stkdevkit/index.htm#stkObjects/ObjectModelTutorial.html

    + https://help.agi.com/stkdevkit/LinkedDocuments/OM_CoverageTutorial.txt

    + https://help.agi.com/stkdevkit/LinkedDocuments/ObjectModelTutorial.txt

        