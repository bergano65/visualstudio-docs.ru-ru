---
title: "Сохранение стандартного документа | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Сохранение документов стандартные редакторы [Visual Studio SDK]"
  - "проекты [Visual Studio SDK] сохранение стандартных документов"
  - "Сохраняемость, сохранение стандартных документов"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Сохранение стандартного документа
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Дескрипторы среды сохранить, сохранить как и сохраняют все команды.  Когда пользователь выбирает **Сохранить**"  **Сохранить как**или  **Сохранить все** от  **Файл** меню или закрывает решение, что приводит к a  **Сохранить все**следующий процесс.  
  
 ![Standard Edition](../../extensibility/internals/media/public.png "Public")  
Сохранить, сохранить как и сохраните всю обработку команд для стандартного редактора  
  
 Этот процесс детализирован в следующих шагах.  
  
1.  После **Сохранить** и  **Сохранить как** выделены команды среды используют  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> служба, чтобы определить окно активного документа и, таким образом, какие элементы должны быть сохранены.  После того как окно активного документа известно, среда находит идентификатор указателей и элемента иерархии \(itemID\) для документа в таблице текущих документов.  Дополнительные сведения см. в разделе [Таблицы запущенных документа](../../extensibility/internals/running-document-table.md).  
  
     После **Сохранить все** команда выбрана среда использует сведения в таблице текущих документа, чтобы компилировать список всех элементов для сохранения.  
  
2.  Если решение возвращает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов он проходит по набору выбранных элементов \(то есть вариантов выбора нескольких элементов, предоставляемых  <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> служба\).  
  
3.  Для каждого элемента в выделении решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод позволяет определить, является ли  **Save** команда меню должна быть включена.  Если один или несколько элементов, пакостны **Save** команда включена.  Если иерархия использует стандартный редактор, то иерархия делегатов запроса пакостного состояния к редактору путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4.  На каждом выбранном элементе, пакостн решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод на соответствующих иерархиях.  
  
     Он применяется для иерархии для использования стандартного редактора изменить документ.  В этом случае объект данных документа для редактора должен поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс.  В начало <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> вызов метода, проект должен быть отчет, что документ сохраняется с помощью редактора  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод объекта данных документа.  Редактор может разрешить среда обработки **Сохранить как** диалоговое окно " вызов  `Query Service` для  <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> интерфейс.  Возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс.  Редактор должен затем вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> метод передачи указатель к редактору  <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> реализация посредством  `pPersistFile` параметр.  Среда затем выполняет операцию сохранения и предоставляет **Сохранить как** диалоговое окно редактора.  Среда затем выполняет обратный вызов в редактор с <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Если пользователь пытается сохранить документ без заголовка \(то есть несохраненные документ ранее\), то команда сохранить как, фактически выполняется.  
  
6.  Для команды сохранить как среда отображает диалоговое окно сохранить как пробуждая пользователя для имени файла.  
  
     Если имя файла изменилось, то иерархия отвечает за обновление информации фрейма документа кэшированные путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\).  
  
 Если **Сохранить как** команда перемещает расположение документа и иерархия чувствительна к расположению документа, а иерархия отвечает за обработка с владения открытого окна документа в другой иерархии.  Например, это происходит, если проект отслеживает, является ли файл внутренний или внешний файл \(произвольный файл\) по отношению к проекту.  Следующая процедура используется для изменения владельца файла в проект прочих файлов.  
  
## Изменить владельца файла  
  
#### Изменить владельца файла в проект прочих файлов  
  
1.  Служба запросов <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> интерфейс.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> возвращает.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`"  `punkWindowFrame`\), чтобы передать документ в новой иерархии.  Иерархия при выполнении команды " сохранить как " вызывает этот метод.  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)