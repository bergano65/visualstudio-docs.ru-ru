---
title: Задача GetWinFXPath | Документация Майкрософт
description: Узнайте, как использовать задачу GetWinFXPath MSBuild, которая возвращает каталог текущей среды выполнения .NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 164f9f91eda1d81db00d25bb4e18a6cbb352e41e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914626"
---
# <a name="getwinfxpath-task"></a>Задача GetWinFXPath

Задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> возвращает каталог текущей среды выполнения .NET.

## <a name="task-parameters"></a>Параметры задачи

| Параметр | Описание |
|-------------------| - |
| `WinFXPath` | Необязательный параметр вывода **String**.<br /><br /> Определяет действительный путь к среде выполнения .NET. |
| `WinFXNativePath` | Обязательный параметр **String**.<br /><br /> Определяет действительный путь к собственной среде выполнения .NET. |
| `WinFXWowPath` | Обязательный параметр **String**.<br /><br /> Определяет путь к сборкам .NET в 32-разрядном модуле **Windows on Windows** в 64-разрядных системах. |

## <a name="remarks"></a>Remarks

 Если задача <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> выполняется в 64-разрядном процессоре, параметру **WinFXPath** присваивается путь, который хранится в параметре **WinFXWowPath**. В противном случае параметру **WinFXPath** присваивается путь, который хранится в параметре **WinFXNativePath**.

## <a name="example"></a>Пример

 В следующем примере показано, как использовать задачу **GetWinFXPath** для определения собственного пути среды выполнения .NET.

```xml
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

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
