---
title: Практическое руководство. Изменение файлов Web.Config для инструментирования и профилирования динамически скомпилированных веб-приложений ASP.NET | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c5cfc94bef15e34deaec9d07a4b66021cb4fc39
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176310"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Практическое руководство. Изменение файлов Web.Config для инструментирования и профилирования динамически скомпилированных веб-приложений ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете использовать метод инструментирования средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для сбора подробных сведений о времени, данных о выделении памяти .NET и данных о времени существования объекта .NET из динамически скомпилированных веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 В этом разделе описывается внесение изменений в файл конфигурации web.config для включения возможности инструментирования и профилирования веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  Изменять файл web.config не требуется при использовании метода профилирования с выборкой или при инструментировании предварительно скомпилированного модуля [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 Корень файла web.config — элемент **configuration**. Для инструментирования и профилирования динамически скомпилированных веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] необходимо добавить или изменить следующие элементы:  
  
-   Элемент **configuration/runtime/assemblyBinding/dependentAssembly**, который идентифицирует сборку Microsoft.VisualStudio.Enterprise.ASPNetHelper, управляющую профилированием. Элемент **dependentAssembly** содержит два дочерних элемента: **assemblyIdentity** и **codeBase**.  
  
-   Элемент **configuration/system.web/compilation**, который определяет шаг компиляции пост-обработки профилировщика для целевой сборки.  
  
-   Два элемента **add**, которые задают расположение средств профилирования, добавляются в раздел **configuration/appSettings**.  
  
 Рекомендуется создать копию исходного файла web.config, который можно использовать для восстановления конфигурации приложения.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Добавление сборки ASPNetHelper как элемента configuration/runtime/assemblyBinding/dependentAssembly  
  
1.  При необходимости добавьте элемент **runtime** как дочерний элемент элемента **configuration**; в противном случае переходите к следующему шагу.  
  
     У элемента **runtime** нет атрибутов. Элемент **configuration** может иметь только один дочерний элемент **runtime**.  
  
2.  При необходимости добавьте элемент **assemblyBinding** как дочерний элемент элемента **runtime**; в противном случае переходите к следующему шагу.  
  
     Элемент **runtime** может иметь только один элемент **assemblyBinding**.  
  
3.  Добавьте следующее имя и значение атрибута в элемент **assemblyBinding**:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn:schemas-microsoft-com:asm.v1**|  
  
4.  Добавьте элемент **dependentAssembly** как дочерний элемент элемента **assemblyBinding**.  
  
     Элемент **dependentAssembly** не имеет атрибутов.  
  
5.  Добавьте элемент **assemblyIdentity** как дочерний элемент элемента **dependentAssembly**.  
  
6.  Добавьте следующие имена и значения атрибутов в элемент **assemblyIdentity**:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7.  Добавьте элемент **codeBase** как дочерний элемент элемента **dependentAssembly**.  
  
8.  Добавьте следующие имена и значения атрибутов в элемент **codeBase**:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` — это URL-адрес файла Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Если файл [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлен в папку по умолчанию, значение **href** должно быть следующим: `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`.  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Добавление шага пост-обработки профилировщика в элемент configuration/system.web/compilation  
  
1.  При необходимости добавьте элемент **system.web** как дочерний элемент элемента **configuration**; в противном случае переходите к следующему шагу.  
  
     У элемента **system.web** нет атрибутов. Элемент **configuration** может иметь только один дочерний элемент **system.web**.  
  
2.  При необходимости добавьте элемент **compilation** как дочерний элемент элемента **system.web**; в противном случае переходите к следующему шагу.  
  
     Элемент **system.web** может иметь только один дочерний элемент **compilation**.  
  
3.  Удалите существующие атрибуты из элемента **compilation** и добавьте следующее имя и значение атрибута:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Добавление параметров расположения профилировщика в элемент configuration/appSettings  
  
1.  При необходимости добавьте элемент **appSettings** как дочерний элемент элемента **configuration**; в противном случае переходите к следующему шагу.  
  
     У элемента **appSettings** нет атрибутов. Элемент **configuration** может иметь только один дочерний элемент **appSettings**.  
  
2.  Добавьте элемент **add** как дочерний элемент элемента **appSettings**.  
  
3.  Добавьте следующие имена и значения атрибутов в элемент **add**:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**значение**|`PerformanceToolsFolder` **\VSInstr.Exe**|  
  
4.  Добавьте еще один элемент **add** как дочерний элемент элемента **appSettings**.  
  
5.  Добавьте следующие имена и значения атрибутов в этот элемент **add**:  
  
    |Имя атрибута|Значение атрибута|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**значение**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` — это путь к исполняемым файлам профилировщика. Если [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] установлен в папку по умолчанию, значением будет **C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools**.  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Пример  
 Ниже приведено полное содержимое файла web.config для включения инструментирования и профилирования динамически скомпилированных веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. В примере предполагается, что перед изменением в файле отсутствовали другие параметры.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор подробных данных о времени](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Практическое руководство. Инструментирование динамически скомпилированного приложения ASP.NET и сбор данных об использовании памяти](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)



