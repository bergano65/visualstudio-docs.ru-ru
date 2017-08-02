---
title: "Сохранение пользовательского документа | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Сохраняемость, сохранение пользовательских документов"
  - "проекты [Visual Studio SDK] Сохранение пользовательских документов"
  - "Сохранение документов пользовательские редакторы [Visual Studio SDK]"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Сохранение пользовательского документа
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Дескрипторы среды **Save**"  **Save As**и  **Save All** команды.  Когда пользователь щелкает **Сохранить**"  **Сохранить как**"  **или сохранить все** на  **Файл** меню или закрывает решение сохранить все, что выполняется следующий процесс.  
  
 ![Сохранение редактора клиента](~/docs/extensibility/internals/media/private.gif "Private")  
Сохранить, сохранить как и сохраните всю обработку команд для специализированного редактора  
  
 Этот процесс детализирован в следующих шагах.  
  
1.  Для **Сохранить** и  **Сохранить как** команды среды используют  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> служба, чтобы определить окно активного документа и, таким образом, какие элементы должны быть сохранены.  После того как окно активного документа известно, среда находит идентификатор указателей и элемента иерархии \(itemID\) для документа в таблице текущих документов.  Дополнительные сведения см. в разделе [Таблицы запущенных документа](../../extensibility/internals/running-document-table.md).  
  
     Для сохранения всю команду среда использует сведения в таблице текущих документа, чтобы компилировать список всех элементов для сохранения.  
  
2.  Если решение возвращает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов он проходит по набору выбранных элементов \(то есть вариантов выбора нескольких элементов, предоставляемых  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> служба\).  
  
3.  Для каждого элемента в выделении решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод позволяет определить, должна ли команда меню сохранения быть включена.  Если один или несколько элементов пакостны, то команда save включена.  Если иерархия использует стандартный редактор, то иерархия делегатов запроса пакостного состояния к редактору путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4.  На каждом выбранном элементе, пакостн решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод на соответствующих иерархиях.  
  
     В случае специализированного редактора, взаимодействие между объектом данных документа и проектом закрыто.  Таким образом, все особые вопросы, связанные с сохраняемости обрабатывается между этими 2 объектами.  
  
    > [!NOTE]
    >  При реализации собственной сохраняемость, не забудьте вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> метод, чтобы сэкономить время.  Этот метод проверяет, чтобы убедиться, что безопасно сохранить файл \(например, файл доступен не только для чтения\).  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)