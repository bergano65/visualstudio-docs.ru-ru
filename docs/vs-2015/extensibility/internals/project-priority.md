---
title: Проект приоритет | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57698e78c9228177e7f078cd725c1d4571e36d76
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571883"
---
# <a name="project-priority"></a>Приоритет проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [приоритет проекта](https://docs.microsoft.com/visualstudio/extensibility/internals/project-priority).  
  
Обычно элемент проекта является членом только один проект в решении. Таким образом интегрированной среды разработки можно легко определить какой проект используется для открытия элемента. Тем не менее если элемент входит в несколько проектов, интегрированная среда разработки использует схему приоритет определить лучший проект для открытия.  
  
 В следующем списке приведены схемы приоритетов проекта:  
  
-   Интегрированная среда разработки вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> метод для каждого проекта в решение, чтобы определить, является ли документ является членом этого проекта.  
  
-   Если документ является членом проекта, проект отвечает с приоритетом назначает что проект в соответствии с его обработка этого документа. Например проект на языке отвечает с высоким приоритетом для его языка исходных файлов, но отвечает с более низким приоритетом для типа нераспознанный файл, который не используется в качестве части процесса построения.  
  
-   Проекты, которые предоставляют пользовательские, конкретного проекта редакторы и конструкторы для документа также получают более высокий приоритет.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Перечисление предоставляет документ значения приоритета.  
  
-   Проект, который указывает наивысший приоритет получает контекст для открытия документа. Если два проекта возвращает значения с одинаковым приоритетом, активным проектом является предпочтительным. Если проект в решении не отвечает, что он может открывать документ, интегрированной среды разработки переводит документ в проект прочих файлов. Дополнительные сведения см. в разделе [прочих файлов](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>См. также  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)   
 [Как: открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)

