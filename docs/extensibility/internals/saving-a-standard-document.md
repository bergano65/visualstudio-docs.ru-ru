---
title: "Сохранение стандартный документ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cdfb4631420f6803e6434bd67b93bd713cfd1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-standard-document"></a>Сохранение стандартного документа
Сохранить, сохранить как и сохранить все команды, обрабатывает среды. Когда пользователь выбирает **Сохранить**, **Сохранить как**, или **сохранить все** из **файл** меню или закрывает решение, в результате чего  **Сохранить все**, происходит следующее.  
  
 ![Стандартный редактор](../../extensibility/internals/media/public.gif "открытый")  
Сохранить, сохранить как и сохранить все обработку команд для стандартного редактора  
  
 Этот процесс подробно описан в следующих шагов:  
  
1.  При **Сохранить** и **Сохранить как** выбраны команды, в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы для определения окна активного документа и таким образом какие элементы должно быть сохранено. После получения окна активного документа среде находит указатель иерархии и идентификатор элемента (itemID) для документа в запущенной таблице документов. Дополнительные сведения см. в разделе [под управлением таблицы Document](../../extensibility/internals/running-document-table.md).  
  
     Когда **сохранить все** выборе команды, среде использует сведения в запущенной таблице документов для компиляции список всех элементов для сохранения.  
  
2.  При получении решения <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, он проходит через набор выбранных элементов (то есть множественный выбор, предоставляемые <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы).  
  
3.  Для каждого элемента в выделенном фрагменте, в решении используется указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод, чтобы определить ли **Сохранить** должна быть включена команда меню. Если один или несколько элементов "грязные", а затем **Сохранить** команда включена. Если иерархия использует стандартного редактора, затем делегаты иерархии, которая запрашивает "грязный" статус к редактору путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.  
  
4.  На каждый выбранный элемент содержит "грязные" в решении используется указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод на соответствующие иерархии.  
  
     Чаще всего для иерархии для использования стандартного редактора для изменения документа. В этом случае объект данных документа, для этого редактор должен поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейса. При получении сообщения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> вызова метода проекта сообщает о редакторе, сохранении документа, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> метод в объект данных документа. Редактор можно разрешить среду для обработки **Сохранить как** диалоговом путем вызова `Query Service` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> интерфейса. Возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейса. Затем необходимо вызвать редактор <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> метод, передавая указатель в редактор <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> реализации с помощью параметра `pPersistFile` параметр. Среды, затем выполняет операции сохранения и предоставляет **Сохранить как** диалоговое окно для редактора. Среда вызывает редактор с <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Если пользователь пытается сохранить документ без имени (то есть ранее несохраненный документ), команда Сохранить как фактически выполняется.  
  
6.  Для «Сохранить как» среды отображается диалоговое окно Сохранить как, запрос на ввод имени файла.  
  
     Если изменилось имя файла, то для рамки документа обновление кэшированных данных путем вызова отвечает иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Если **Сохранить как** команда перемещает расположение документа и иерархии чувствительна к расположению документа, а затем иерархии отвечает за передачей владения на открытое окно документа в другой иерархии. Например это происходит, если проект отслеживает, является ли файл внутреннего или внешнего файла (файл) относительно проекта. Используйте следующую процедуру для изменения владельца файла в проект прочие файлы.  
  
## <a name="changing-file-ownership"></a>Смена владельца файла  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Чтобы изменить владельца файлов в проект прочие файлы  
  
1.  Запрос службы для <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> интерфейса.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> возвращается.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) метод, чтобы передать документ в новой иерархии. Этот метод вызывается при выполнении команды «Сохранить как» иерархии.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)