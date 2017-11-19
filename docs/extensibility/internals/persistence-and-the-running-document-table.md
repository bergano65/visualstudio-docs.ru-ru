---
title: "Сохраняемости и запуском документа таблицы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 062c623ec1de779733e41a8abcad8ca478155dba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="persistence-and-the-running-document-table"></a>Сохранение состояния и выполнения таблицы Document
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, проекты, полностью отвечает за управление сохраняемости их элементов проекта, которые они выполняют с помощью службы, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Документы являются основными единицами организации сохраняемости в среде Visual Studio. Проекты координировать открытие, сохранение и переименование документов с запущенной таблице документов (RDT), ресурс, который отслеживает состояние всех открытых документов.  
  
## <a name="managing-persistence"></a>Управление сохраняемости  
 Проекты управлять службы постоянного хранения среды с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> интерфейса. Хотя среды напрямую никогда не запрашивает документ для сохраниться, он запрашивает у владельца проекта (или иерархия) для сохранения документа. Это позволяет проекта для сохранения его данных элемента проекта в локальные файлы, удаленные файлы, базы данных, хранилище или другой носитель.  
  
 Глобальной среде поддерживает RDT. Среда поддерживает записи для всех открытых окон и документы в RDT, что позволяет им получать специальные уведомления, например, при закрытии решения. Кроме того, RDT позволяет отслеживать их соответствующие узлы в среде **обозревателе решений**. RDT хранит одну запись для каждой открытой, сохраняемого объекта, включая файлы проектов и элементов проектов документов.  
  
## <a name="see-also"></a>См. также  
 [Запуска таблицы документов](../../extensibility/internals/running-document-table.md)   
 [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)