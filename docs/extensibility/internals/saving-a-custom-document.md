---
title: Сохранение настраиваемого документа | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724077"
---
# <a name="saving-a-custom-document"></a>Сохранение настраиваемого документа
Среда обрабатывает команды **сохранить**, **Сохранить как**и **сохранить все** . Когда пользователь нажимает кнопку **сохранить**, **Сохранить как** **или сохранить все** в меню **файл** или закрывает решение, в результате чего происходит сохранение всего процесса.

 ![Сохранение в редакторе клиентов](../../extensibility/internals/media/private.gif "Private") Сохранение, сохранение как и сохранение всей обработки команд для пользовательского редактора

 Этот процесс описан в следующих шагах.

1. Для команд **сохранить** и **Сохранить как** среда использует службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> для определения активного окна документа и, таким образом, элементы, которые следует сохранить. Когда окно активного документа будет известно, среда находит указатель иерархии и идентификатор элемента (itemID) для документа в выполняемой таблице документов. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).

     Для команды сохранить все среда использует сведения из таблицы выполняемого документа для компиляции списка всех элементов для сохранения.

2. Когда решение получает вызов <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, оно выполняет итерацию по набору выбранных элементов (то есть множественный выбор, предоставленный службой <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. В каждом выбранном элементе решение использует указатель иерархии для вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>, чтобы определить, должна ли быть включена команда меню "Сохранить". Если один или несколько элементов являются "грязными", команда "Сохранить" будет включена. Если в иерархии используется стандартный редактор, то иерархия делегирует запрос о состоянии "грязного" в редактор, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> в соответствующих иерархиях.

     В случае с пользовательским редактором связь между объектом данных документа и проектом является закрытой. Таким же, все специальные проблемы сохраняемости обрабатываются между этими двумя объектами.

    > [!NOTE]
    > При реализации собственного сохраняемости обязательно вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>, чтобы сэкономить время. Этот метод проверяет, является ли сохранение файла защищенным (например, если файл не доступен только для чтения).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)