---
title: "Типы файлов проектов и решений | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 744b35962a196e0372d1bd1fa916f247a9195da6
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
# <a name="project-and-solution-file-types"></a>Типы файлов проектов и решений
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает многие типы файлов. В определенной установке поддерживаемые типы файлы определяются установленными компонентами. В этом разделе перечислены типы файлов решений и проектов, которые поддерживаются в некоторых типичных установках. Для сведения о других типах файлов выполните поиск каждого типа по расширению файла.  
  
## <a name="solution-files-sln-and-suo"></a>Файлы решений (.SLN и .SUO)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует два типа файлов (.SLN и .SUO) для хранения параметров, связанных с решениями. Эти файлы, которые называют файлами решений, предоставляют Обозревателю решений информацию, необходимую для отображения графического интерфейса, используемого для управления файлами. Они позволяют сконцентрироваться на проектах и конечных целях, а не на самой среде при каждом возврате к задачам разработки.  
  
|Расширение|Имя|Описание|  
|---------------|----------|-----------------|  
|.SLN|Решение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]|Организует проекты, элементы проектов и решений в решение.|  
|SUO|Параметры пользователя решения|Отслеживает настройки на уровне пользователя в Visual Studio, такие как контрольные точки.|  
  
## <a name="project-files"></a>Файлы проекта  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использует различные форматы файлов для хранения сведений, связанных с проектами. Дополнительные сведения см. в следующих разделах справки:  
  
 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]  
 [Типы файлов, создаваемых для проектов Visual C++](/cpp/ide/file-types-created-for-visual-cpp-projects)    
 [Создание проектов Visual C++ и управление ими](/cpp/ide/creating-and-managing-visual-cpp-projects)    
 [Юникод](/cpp/mfc/unicode-in-mfc)  
  
## <a name="see-also"></a>См. также  
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)