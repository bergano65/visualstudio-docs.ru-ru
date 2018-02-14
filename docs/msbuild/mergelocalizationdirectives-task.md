---
title: "Задача MergeLocalizationDirectives | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b8e53bcb94c753659848b336be243a2c582fc0c2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="mergelocalizationdirectives-task"></a>Задача MergeLocalizationDirectives
Задача <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> выполняет слияние атрибутов локализации и заметок одного или нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в один файл для всей сборки.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Обязательный параметр **ITaskItem[]**.<br /><br /> Определяет список файлов директив локализации для отдельных файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputFile`|Обязательный параметр вывода **String**.<br /><br /> Определяет выходной путь скомпилированной сборки директив локализации.|  
  
## <a name="remarks"></a>Примечания  
 Вы можете добавлять комментарии и атрибуты локализации к содержимому [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]. Благодаря поддержке локализации [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] можно удалить комментарии и атрибуты локализации, поместив их в LOC-файл отдельно от созданной сборки. Это можно сделать с помощью атрибута **LocalizationPropertyStorage**. См. дополнительные сведения об атрибуте **LocalizationPropertyStorage** в разделе, посвященном [комментариям и атрибутам локализации](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется слияние комментариев локализации нескольких файлов [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в двоичном формате в один LOC-файл.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)