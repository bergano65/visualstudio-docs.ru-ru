---
title: Задача UidManager | Документация Майкрософт
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93b3c571d8c68eee8ee00475fad8bda2b5b2ec65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989139"
---
# <a name="uidmanager-task"></a>Задача UidManager
Задача <xref:Microsoft.Build.Tasks.Windows.UidManager> проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], включенных в исходные файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
  
| Параметр | Описание |
|-------------------------| - |
| `IntermediateDirectory` | Необязательный параметр типа **String**.<br /><br /> Определяет каталог, используемый для резервного копирования файлов источника [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], которые указываются с помощью параметра **MarkupFiles**. |
| `MarkupFiles` | Обязательный параметр **ITaskItem[]**.<br /><br /> Определяет файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] источника, включаемые для проверки, обновления или удаления UID. |
| `Task` | Обязательный параметр **string**.<br /><br /> Определяет задачу управления UID для выполнения. Допустимые параметры: **Check**, **Update** и **Remove**. |
  
## <a name="example"></a>Пример  
 В следующем примере задача <xref:Microsoft.Build.Tasks.Windows.UidManager> используется для проверки того, что файлы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] указанного источника содержат элементы [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] с соответствующими UID.  
  
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
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Практическое руководство. Локализация приложения](/dotnet/framework/wpf/advanced/how-to-localize-an-application)