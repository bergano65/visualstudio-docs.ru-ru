---
title: Сохранение стандартного документа | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ced873db6c1a3c9adbe40625ed44817eb6703d9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614900"
---
# <a name="saving-a-standard-document"></a>Сохранение стандартного документа
Эти задачи выполняет среда сохранение, сохранение и сохранить все команды. Когда пользователь выбирает **Сохранить**, **Сохранить как**, или **сохранить все** из **файл** меню или закрывает решение, в результате чего  **Сохранить все**, происходит следующее.

 ![Стандартный редактор](../../extensibility/internals/media/public.gif "открытый") сохранение, сохранение и сохранить все обработки команд для стандартного редактора

 Этот процесс подробно описан в следующих шагах:

1. Когда **Сохранить** и **Сохранить как** выбраны команды, в среде используется <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы для определения активного окна документа, и таким образом следует сохранить какие элементы. После получения активном окне документа среды находит указатель иерархии и идентификатор элемента (itemID) для документа в таблице выполняющихся документов. Дополнительные сведения см. в разделе [таблице выполняющихся документов](../../extensibility/internals/running-document-table.md).

    Когда **сохранить все** установлен, в среде используется данные в таблице выполняющихся документов для компиляции список всех элементов, чтобы сохранить.

2. При получении решение <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызова, он проходит по коллекции набор выбранных элементов (то есть множественного выбора, предоставляемыми <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы).

3. Для каждого элемента в выделении, решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> метод для определения ли **Сохранить** должна быть включена команда меню. Если один или несколько элементов "грязные", а затем **Сохранить** команда включена. Если в иерархии используется стандартный редактор, затем делегаты иерархии, запрашивая "грязных" состояние в редактор, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> метод.

4. Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> метод соответствующие иерархий.

    Довольно часто для иерархии, чтобы использовать стандартный редактор для редактирования документа. В этом случае объект данных документа, для этого редактор должен поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> интерфейс. При получении сообщения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> вызова метода, проект должен информировать редактора, документ сохраняется путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> метод в объекте данных документа. Редактор позволяет среде, чтобы обрабатывать **Сохранить как** диалоговое окно, путем вызова `Query Service` для <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> интерфейс. Возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс. Затем необходимо вызвать редактор <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , передавая указатель в редактор <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> реализации с помощью параметра `pPersistFile` параметр. Среды, затем выполняет операции сохранения и предоставляет **Сохранить как** диалоговое окно для редактора. Среды затем выполняет обратный вызов в редакторе <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Если пользователь пытается сохранить документ без имени (то есть ранее несохраненный документ), то команда Сохранить как фактически выполняется.

6. Для команды «Сохранить как» среды отображает диалоговое окно Сохранить как, запрос на ввод имени файла.

    Если изменилось имя файла, то для обновления фрейм документа кэшированные данные путем вызова отвечает иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).

   Если **Сохранить как** команда перемещает расположение документа и иерархии чувствительна к местоположение документа, а затем иерархии отвечает за передачей владения на открытое окно документа в другой иерархии. Например это происходит, если проект отслеживает, является ли файл внутреннего или внешнего файла (файл) по отношению к проекта. Используйте следующую процедуру для изменения владельца файла для проекта прочих файлов.

## <a name="changing-file-ownership"></a>Смена владельца файла

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Чтобы изменить владельца файла для проекта прочих файлов

1.  Запроса службе <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> интерфейс.

     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> возвращается.

2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) метод, чтобы передать документ в новой иерархии. Этот метод вызывается в иерархии, выполнение команды «Сохранить как».

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)