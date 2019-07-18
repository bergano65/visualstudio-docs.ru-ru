---
title: Задача UidManager | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5fd8175911def7fb1b63dc63d967c404d649e9e4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703696"
---
# <a name="uidmanager-task"></a>Задача UidManager
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.UidManager> проверяет, обновляет или удаляет уникальные идентификаторы (UID) для локализации всех элементов [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)], включенных в исходные файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`IntermediateDirectory`|Необязательный параметр типа **String**.<br /><br /> Определяет каталог, используемый для резервного копирования файлов источника [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)], которые указываются с помощью параметра **MarkupFiles**.|  
|`MarkupFiles`|Обязательный параметр **ITaskItem[]**.<br /><br /> Определяет файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] источника, включаемые для проверки, обновления или удаления UID.|  
|`Task`|Обязательный параметр **string**.<br /><br /> Определяет задачу управления UID для выполнения. Допустимые параметры: **Check**, **Update** и **Remove**.|  
  
## <a name="example"></a>Пример  
 В следующем примере задача <xref:Microsoft.Build.Tasks.Windows.UidManager> используется для проверки того, что файлы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] указанного источника содержат элементы [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] с соответствующими UID.  
  
```  
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
 [Построение приложения WPF](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Практическое руководство. Локализация приложения](https://msdn.microsoft.com/library/5001227e-9326-48a4-9dcd-ba1b89ee6653)
