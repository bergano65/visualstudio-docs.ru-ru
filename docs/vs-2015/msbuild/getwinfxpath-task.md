---
title: Задача GetWinFXPath | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21aa8cd81465917c33709b751ba2e206e7d7484d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561645"
---
# <a name="getwinfxpath-task"></a>Задача GetWinFXPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача GetWinFXPath](https://docs.microsoft.com/visualstudio/msbuild/getwinfxpath-task).  
  
  
Задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> возвращает каталог текущей среды выполнения [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WinFXPath`|Необязательный параметр вывода **String**.<br /><br /> Определяет действительный путь к среде выполнения [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)].|  
|`WinFXNativePath`|Обязательный параметр **string**.<br /><br /> Определяет действительный путь к собственной среде выполнения [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)].|  
|`WinFXWowPath`|Обязательный параметр **string**.<br /><br /> Определяет путь к сборкам [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] в 32-разрядном модуле **Windows on Windows** в 64-разрядных системах.|  
  
## <a name="remarks"></a>Примечания  
 Если задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> выполняется в 64-разрядном процессоре, параметру **WinFXPath** присваивается путь, который хранится в параметре **WinFXWowPath**. В противном случае параметру **WinFXPath** присваивается путь, который хранится в параметре **WinFXNativePath**.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать задачу **GetWinFXPath** для определения собственного пути среды выполнения [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



