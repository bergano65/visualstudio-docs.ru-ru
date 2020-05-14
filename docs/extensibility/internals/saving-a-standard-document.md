---
title: Сохранение стандартного документа Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705551"
---
# <a name="saving-a-standard-document"></a>Сохранение стандартного документа
Среда обрабатывает команды «Сохранить», «Сохранить как» и «Сохранить все команды». Когда пользователь выбирает **Сохранить,** **Сохранить как**, или сохранить **все** из меню **файла** или закрывает решение, в результате чего **Сохранить все**, следующий процесс происходит.

 ![Стандартный редактор](../../extensibility/internals/media/public.gif "Public") Сохранить, сохранить, сохранить как и сохранить все обработки команд для стандартного редактора

 Этот процесс подробно описан в следующих шагах:

1. При выборе команд **«Сохранение** и **сохранение»** среда <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> использует службу для определения окна активного документа и, таким образом, элементы должны быть сохранены. Как только известно окно активного документа, среда находит указатель иерархии и идентификатор элементов (itemID) для документа в таблице запущенных документов. Для получения дополнительной информации [см.](../../extensibility/internals/running-document-table.md)

    При выборе команды **«Сохранить все»** среда использует информацию в таблице исходного документа для составления списка всех элементов для сохранения.

2. Когда решение получает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, оно итерируется через набор выбранных элементов (т.е. несколько вариантов, выставленных службой). <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>

3. На каждом элементе в выборе решение использует указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> иерархии для вызова метода, чтобы определить, следует ли включена команда меню **«Сохранить».** Если один или несколько элементов являются грязными, то включена команда **Сохранить.** Если иерархия использует стандартный редактор, то иерархия делегирует запрос на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> получение грязного статуса к редактору, вызывая метод.

4. На каждом выбранном элементе, который является грязным, решение <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> использует указатель иерархии для вызова метода на соответствующих иерархиях.

    Обычно иерархия использует стандартный редактор для ред., чтобы отредовать документ. В этом случае объект данных документа для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> этого редактора должен поддерживать интерфейс. После получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> вызова метода проект должен сообщить редактору о <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> том, что документ сохраняется, вызывая метод на объект данных документа. Редактор может позволить среде обрабатывать поле диалога **Save As,** вызывая `Query Service` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> интерфейс. Это возвращает указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> к интерфейсу. Затем редактор должен <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> вызвать метод, передав указатель на реализацию редактора <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> с помощью `pPersistFile` параметра. Затем среда выполняет операцию «Сохранение» и предоставляет для редактора диалоговую будку **«Сохранить как** диалог». Окружающая среда затем перезванивает редактору с <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Если пользователь пытается сохранить безымянный документ (т.е. ранее не сохраненный документ), то на самом деле выполняется команда «Сохранить как элемент».

6. Для команды Save As среда отображает диалоговый ящик «Сохранить как диалог», что дает пользователю имя файла.

    Если имя файла изменено, иерархия отвечает за обновление кэшированной информации <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>кадра документа по вызову (VSFPROPID_MkDocument).

   Если команда **«Сохранение как»** перемещает местоположение документа, а иерархия чувствительна к местоположению документа, иерархия отвечает за передачу права собственности на окно открытого документа другой иерархии. Например, это происходит, если проект отслеживает, является ли файл внутренним или внешним файлом (Разный файл) по отношению к проекту. Используйте следующую процедуру, чтобы изменить право собственности на файл в проект «Разные файлы».

## <a name="changing-file-ownership"></a>Изменение владения файлами

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Изменение права собственности на файлы в проект «Разные файлы»

1. Служба запроса <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> для интерфейса.

     Возвращается <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> указатель.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> Вызовите`pszMkDocumentNew` `punkWindowFrame`метод () для переноса документа в новую иерархию. Иерархия, выполняющая команду «Сохранение как», вызывает этот метод.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
