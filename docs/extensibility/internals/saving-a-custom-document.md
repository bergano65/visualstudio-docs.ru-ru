---
title: "Сохранение пользовательского документа | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2b19c6ba222644bc9d5fb97874f50bf6a6aa59d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-custom-document"></a>Сохранение пользовательского документа
Дескрипторы среды **Сохранить**, **Сохранить как**, и **сохранить все** команд. Когда пользователь щелкает **Сохранить**, **Сохранить как**, **или сохранить все** на **файл** меню или закрывает решение, приведет к сохранить все, следующие процесс выполняется.  
  
 ![Сохранение редактора клиента](../../extensibility/internals/media/private.gif "закрытый")  
Сохранить, сохранить как и сохранить все обработку команд для пользовательского редактора  
  
 Этот процесс подробно описан в следующих шагов:  
  
1.  Для **Сохранить** и **Сохранить как** команд в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы для определения окна активного документа и таким образом какие элементы должно быть сохранено. После получения окна активного документа среде находит указатель иерархии и идентификатор элемента (itemID) для документа в запущенной таблице документов. Дополнительные сведения см. в разделе [под управлением таблицы Document](../../extensibility/internals/running-document-table.md).  
  
     Сохранить все команды среды использует для компиляции список всех элементов, чтобы сохранить данные в запущенной таблице документов.  
  
2.  При получении решения <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, он проходит через набор выбранных элементов (то есть множественный выбор, предоставляемые <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы).  
  
3.  Для каждого элемента в выделенном фрагменте, в решении используется указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод, чтобы определить, включена ли команды меню "Сохранить". Если один или несколько элементов «грязных», команды «Сохранить» включена. Если иерархия использует стандартного редактора, затем делегаты иерархии, которая запрашивает "грязный" статус к редактору путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4.  На каждый выбранный элемент содержит "грязные" в решении используется указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод на соответствующие иерархии.  
  
     В случае пользовательский редактор связи между объектом данных документа и проект является закрытым. Таким образом любые проблемы специальные сохраняемости обрабатываются между этими двумя объектами.  
  
    > [!NOTE]
    >  Если вы реализуете собственную сохраняемости, необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> метод, чтобы сэкономить время. Этот метод проверяет, чтобы убедиться в том, что можно безопасно сохранить файл (например, файл не только для чтения).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)