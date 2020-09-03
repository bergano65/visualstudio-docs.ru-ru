---
title: Типы файлов проектов и решений | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- suo files
- file types, Visual Studio
- file extensions
- solutions, solution files
- solution files
- .sln files
- Visual Studio, file types and extensions
- extensions, file types
- sln files
- .suo files
- file extensions, Visual Studio
- file types
ms.assetid: 0ba5007b-465d-4efa-b1e4-f0ee68527649
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59f9fb1f628da6bc4d958fdca3843adebe61b798
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662141"
---
# <a name="project-and-solution-file-types"></a>Типы файлов проектов и решений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает многие типы файлов. В определенной установке поддерживаемые типы файлы определяются установленными компонентами. В этом разделе перечислены типы файлов решений и проектов, которые поддерживаются в некоторых типичных установках. Для сведения о других типах файлов выполните поиск каждого типа по расширению файла.

## <a name="solution-files-sln-and-suo"></a>Файлы решений (.SLN и .SUO)
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использует два типа файлов (.SLN и .SUO) для хранения параметров, связанных с решениями. Эти файлы, которые называют файлами решений, предоставляют Обозревателю решений информацию, необходимую для отображения графического интерфейса, используемого для управления файлами. Они позволяют сконцентрироваться на проектах и конечных целях, а не на самой среде при каждом возврате к задачам разработки.

|Расширение|name|Описание|
|---------------|----------|-----------------|
|.SLN|Решение [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]|Организует проекты, элементы проектов и решений в решение.|
|SUO|Параметры пользователя решения|Отслеживает настройки на уровне пользователя в Visual Studio, такие как контрольные точки.|

## <a name="project-files"></a>Файлы проекта
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использует различные форматы файлов для хранения сведений, связанных с проектами. Дополнительные сведения см. в следующих разделах справки:

 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]
 [Типы файлов, создаваемых для проектов Visual C++](https://msdn.microsoft.com/library/2b0ee2e0-ae81-4185-9bb9-11da3c99a283)

 [Creating and Managing Visual C++ Projects](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)

 [Юникод](https://msdn.microsoft.com/library/1002004b-4113-4380-bf63-e1570934b793)

## <a name="see-also"></a>См. также:
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)
