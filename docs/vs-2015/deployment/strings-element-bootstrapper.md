---
title: '&lt;Строки&gt; элемент (загрузчик) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 76946d04bb8afbe70c599516fc110fcccc8f87c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570372"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Строки&gt; элемент (установщик)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;строки&gt; элемент (загрузчик)](https://docs.microsoft.com/visualstudio/deployment/strings-element-bootstrapper).  
  
Определяет локализованные строки названий продуктов, имена пакетов и сообщения об ошибках установки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `Strings` Элемент является дочерним элементом `Package` элемент. Он не имеет атрибутов.  
  
## <a name="string"></a>String  
 `String` Элемент является дочерним элементом `Strings` элемент. Объект `Strings` элемент может иметь один или несколько `String` элементов.  
  
 `String` содержит следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Имя строки.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода указывает, все строки на английском языке для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] установщика.  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## <a name="see-also"></a>См. также  
 [\<Пакет > элемент](../deployment/package-element-bootstrapper.md)



