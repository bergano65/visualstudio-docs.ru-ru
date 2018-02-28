---
title: "Проект приоритет | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ae692249ea952970b096825c8f6968158eb2f17f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="project-priority"></a>Приоритет проекта
Обычно элемент проекта является членом только один проект в решении. Таким образом интегрированной среды разработки можно легко определить, какой проект используется для открытия элемента. Тем не менее если элемент входит в несколько проектов, IDE использует схему приоритет для определения наиболее проект для открытия элемента.  
  
 В следующем списке приведены схемы приоритета проекта:  
  
-   Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> метод для каждого проекта в решение, чтобы определить, является ли документ является членом этого проекта.  
  
-   Если документ является элементом проекта, проекта отвечает с приоритетом назначает, проект в соответствии с его обработка этого документа. Например проекта на языке отвечает с высоким приоритетом для своего языка исходных файлов, но отвечает с более низким приоритетом для типа нераспознанный файл, который не используется в процессе ее построения.  
  
-   Проекты, которые предоставляют пользовательские, конкретного проекта редакторы и конструкторы для документа также получают более высокий приоритет.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Перечисление предоставляет документа значения приоритета.  
  
-   Проект, который определяет самый высокий приоритет предоставляется контекст для открытия документа. Если два проекта возвращают значения приоритетов равны, предпочтительнее активного проекта. Если проект в решении не отвечает, что его можно открыть документ, интегрированной среды разработки переводит документ в прочих файлах проекта. Дополнительные сведения см. в разделе [Miscellaneous Files Project](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>См. также  
 [Прочие файлы проекта](../../extensibility/internals/miscellaneous-files-project.md)   
 [Как: открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)