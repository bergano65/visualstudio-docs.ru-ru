---
title: Файлы TARGETS в MSBuild | Документы Майкрософт
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842880"
---
# <a name="msbuild-targets-files"></a>Файлы Targets в MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] включает в себя несколько TARGETS-файлов, содержащих элементы, свойства, целевые объекты и задачи для обычных сценариев. Эти файлы автоматически импортируются в большинство файлов проекта [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для упрощения обслуживания и повышения удобочитаемости.  
  
 Обычно проекты импортируют один или несколько TARGETS-файлов для определения своего процесса сборки. Например, проект [!INCLUDE[csprcs](../includes/csprcs-md.md)], созданный с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], будет импортировать Microsoft.CSharp.targets, который импортирует файл Microsoft.Common.targets. Сам проект [!INCLUDE[csprcs](../includes/csprcs-md.md)] будет определять элементы и свойства, относящиеся к данному проекту, а стандартные правила сборки для проекта [!INCLUDE[csprcs](../includes/csprcs-md.md)] определяются в импортированных TARGETS-файлах.  
  
 Значение `$(MSBuildToolsPath)` определяет путь к этим общим TARGETS-файлам. Если `ToolsVersion` 4.0, файлы находятся в следующей папке: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Дополнительные сведения о создании собственных целевых объектов см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md). Сведения об использовании `Import` элемента для вставки файла проекта в другой файл проекта см. в разделе [элемент Import (MSBuild)](../msbuild/import-element-msbuild.md) и [Пошаговое руководство. Использование одного и того же целевого объекта в нескольких файлах проекта](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Общие файлы TARGETS  
  
|Файл TARGETS|Описание|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Определяет этапы стандартного процесса сборки для проектов [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../includes/csprcs-md.md)].<br /><br /> Импортированы с помощью файлов Microsoft.CSharp.targets и Microsoft.VisualBasic.targets, которые включают в себя следующую инструкцию: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Определяет этапы стандартного процесса сборки для проектов Visual C#.<br /><br /> Импортированы с помощью файлов проекта Visual C# (с расширением CSPROJ), которые включают в себя следующую инструкцию: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Определяет этапы стандартного процесса сборки для проектов Visual Basic.<br /><br /> Импортированы с помощью файлов проекта Visual Basic (с расширением VBPROJ), которые включают в себя следующую инструкцию: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>См. также:  
 [Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
