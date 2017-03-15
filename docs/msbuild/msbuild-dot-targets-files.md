---
title: "Файлы TARGETS в MSBuild | Документы Майкрософт"
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 17
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
ms.openlocfilehash: e47709e23ae963a9339499eb1b1e1d28834be5bf
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-targets-files"></a>Файлы Targets в MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] включает в себя несколько TARGETS-файлов, содержащих элементы, свойства, целевые объекты и задачи для обычных сценариев. Эти файлы автоматически импортируются в большинство файлов проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для упрощения обслуживания и повышения удобочитаемости.  
  
 Обычно проекты импортируют один или несколько TARGETS-файлов для определения своего процесса сборки. Например, проект [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], созданный с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], будет импортировать Microsoft.CSharp.targets, который импортирует файл Microsoft.Common.targets. Сам проект [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] будет определять элементы и свойства, относящиеся к данному проекту, а стандартные правила сборки для проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] определяются в импортированных TARGETS-файлах.  
  
 Значение `$(MSBuildToolsPath)` определяет путь к этим общим TARGETS-файлам. Если `ToolsVersion` 4.0, файлы находятся в следующей папке: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Дополнительные сведения о создании собственных целевых объектов см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md). Сведения об использовании элемента `Import` для вставки файла проекта в другой файл проекта см. в разделе [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md) и [Практическое руководство. Использование одного и того же целевого объекта в нескольких файлах проектов](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Общие файлы TARGETS  
  
|Файл TARGETS|Описание|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Определяет этапы стандартного процесса сборки для проектов [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Импортированы с помощью файлов Microsoft.CSharp.targets и Microsoft.VisualBasic.targets, которые включают в себя следующую инструкцию: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Определяет этапы стандартного процесса сборки для проектов Visual C#.<br /><br /> Импортированы с помощью файлов проекта Visual C# (с расширением CSPROJ), которые включают в себя следующую инструкцию: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Определяет этапы стандартного процесса сборки для проектов Visual Basic.<br /><br /> Импортированы с помощью файлов проекта Visual Basic (с расширением VBPROJ), которые включают в себя следующую инструкцию: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>См. также  
 [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
