---
title: Задача UidManager | Документация Майкрософт
description: Узнайте, как задача UidManager в MSBuild проверяет, обновляет и удаляет уникальные идентификаторы (UID) для локализации всех элементов XAML в исходных файлах XAML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6287abee811d406ef7aafa5ce3cc3dc62624b0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902620"
---
# <a name="uidmanager-task"></a>Задача UidManager

Задача <xref:Microsoft.Build.Tasks.Windows.UidManager> проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов MSBuild, включенных в исходные файлы MSBuild.

## <a name="task-parameters"></a>Параметры задачи

| Параметр | Описание |
|-------------------------| - |
| `IntermediateDirectory` | Необязательный параметр **String** .<br /><br /> Определяет каталог, используемый для резервного копирования файлов источника XAML, которые указываются с помощью параметра **MarkupFiles**. |
| `MarkupFiles` | Обязательный параметр **ITaskItem[]** .<br /><br /> Определяет файлы XAML источника, включаемые для проверки, обновления или удаления UID. |
| `Task` | Обязательный параметр **String**.<br /><br /> Определяет задачу управления UID для выполнения. Допустимые параметры: **Check**, **Update** и **Remove**. |

## <a name="example"></a>Пример

 В следующем примере задача <xref:Microsoft.Build.Tasks.Windows.UidManager> используется для проверки того, что файлы XAML указанного источника содержат элементы XAML с соответствующими UID.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Практическое руководство. Локализация приложения](/dotnet/framework/wpf/advanced/how-to-localize-an-application)