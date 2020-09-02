---
title: Задача FileClassifier | Документация Майкрософт
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
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2077b1df6d6362c924527e296d36c041e7bd9929
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693785"
---
# <a name="fileclassifier-task"></a>Задача FileClassifier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.FileClassifier> классифицирует набор исходных ресурсов как ресурсов, которые будут внедрены в сборку. Если ресурс является нелокализуемым, он внедряется в основную сборку приложения, в противном случае — во вспомогательную сборку.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Description|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Не используется.|  
|`CLRResourceFiles`|Не используется.|  
|`CLRSatelliteEmbeddedResource`|Не используется.|  
|`Culture`|Необязательный параметр **String** .<br /><br /> Задает язык и региональные параметры для сборки. Он может иметь значение **NULL**, если сборка не подлежит локализации. Если указано значение **NULL**, по умолчанию используется значение, возвращаемое **CultureInfo.InvariantCulture**, в нижнем регистре.|  
|`MainEmbeddedFiles`|Необязательный параметр вывода **ITaskItem[]** .<br /><br /> Указывает нелокализуемые ресурсы, которые внедряются в основную сборку.|  
|`OutputType`|Обязательный параметр **string**.<br /><br /> Задает тип файла, в который будут внедряться указанные исходные файлы. Допустимые значения: **exe**, **winexe**, или **library**.|  
|`SatelliteEmbeddedFiles`|Необязательный параметр вывода **ITaskItem[]** .<br /><br /> Указывает локализуемые файлы, которые внедряются во вспомогательную сборку для языка и региональных параметров, указанных в параметре **Culture**.|  
|`SourceFiles`|Обязательный параметр **ITaskItem[]** .<br /><br /> Задает список файлов для классификации.|  
  
## <a name="remarks"></a>Remarks  
 Если не задан параметр **Culture**, то все ресурсы, указанные с помощью параметра **SourceFiles**, считаются нелокализуемыми. В противном случае они считаются локализуемыми, если не связаны с атрибутом **Localizable**, который имеет значение **false**.  
  
## <a name="example"></a>Пример  
 Следующий пример классифицирует один исходный файл как ресурс и внедряет его во вспомогательную сборку для языка "Французский (Канада)".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по MSBuild для WPF](../msbuild/wpf-msbuild-reference.md)   
 [Справочник по задачам](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)   
 [Создание приложения WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
