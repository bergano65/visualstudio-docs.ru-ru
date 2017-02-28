---
title: "Новые возможности MSBuild 12.0 | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: d299c4959ddf23a8c249f5577ee03fda99e636f7
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-msbuild-120"></a>Новые возможности MSBuild 12.0
MSBuild теперь устанавливается вместе с Visual Studio, а не в составе платформы .NET Framework. Номер текущей версии MSBuild — 12.0. Если вы хотите установить MSBuild отдельно, скачайте пакет установки на странице [скачиваемых материалов MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Измененный путь  
 Теперь MSBuild устанавливается непосредственно в каталог *%ProgramFiles%* — например, в C:\Program Files\MSBuild\\.  
  
## <a name="changed-properties"></a>Измененные свойства  
 В связи с выходом нового номера версии изменены следующие свойства MSBuild:  
  
-   `MSBuildToolsVersion` для этой версии средств — 12.0.  
  
-   Теперь `MSBuildToolsPath` — %ProgramFiles%\MSBuild\12.0\bin в 32-разрядных операционных системах или %ProgramFiles%\MSBuild\12.0\bin\amd64 в 64-разрядных операционных системах.  
  
-   Значения `ToolsVersion` можно найти в HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 в 32-разрядных операционных системах или в HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 в 64-разрядных операционных системах.  
  
-   Свойства `SDK35ToolsPath` и `SDK40ToolsPath` свойства указывают на пакет SDK для .NET Framework, поставляемый с данной версией Visual Studio (например, 8.1A для инструментов 4.X).  
  
## <a name="new-properties"></a>Новые свойства  
  
-   `MSBuildFrameworkToolsPath` является новым свойством со значением %windir%\Microsoft.NET\Framework\v4.0.30319 в 32-разрядных операционных системах или %windir%\Microsoft.NET\Framework64\v4.0.30319 в 64-разрядных операционных системах. Оно заменяет свойство `MSBuildToolsPath`, которое может использоваться для указания на инструменты и служебные программы .NET Framework.  
  
-   Свойства `MSBuildToolsPath` и `MSBuildFrameworkToolsPath` имеют 32-разрядные эквиваленты — `MSBuildToolsPath32` и `MSBuildFrameworkToolsPath32`, — которые всегда указывают на расположение 32-разрядной версии независимо от того, используется ли 32-разрядная или 64-разрядная версия MSBuild.

## <a name="see-also"></a>См. также
[MSBuild](../msbuild/msbuild.md)
