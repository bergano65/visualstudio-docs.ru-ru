---
title: "Задача MergeLocalizationDirectives | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 5
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: e56ad5826bd6d18bd4409e98f8d54c49d266af82
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# <a name="mergelocalizationdirectives-task"></a>Задача MergeLocalizationDirectives
Задача <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> выполняет слияние атрибутов локализации и заметок одного или нескольких файлов в двоичном формате [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] в один файл для всей сборки.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
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
