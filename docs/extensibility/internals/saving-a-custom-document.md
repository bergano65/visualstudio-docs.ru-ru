---
title: Сохранение пользовательского документа Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705613"
---
# <a name="saving-a-custom-document"></a>Сохранение настраиваемого документа
Среда обрабатывает **Сохранение,** **Сохранение как**и **сохранить все** команды. Когда пользователь нажимает **Сохранить,** **Сохранить как** **, или сохранить все** в меню **файла** или закрывает решение, в результате чего Сохранить все, следующий процесс происходит.

 ![Клиент Редактор Сохранить](../../extensibility/internals/media/private.gif "Private") Сохранить, сохранить, сохранить, как и сохранить все обработки команд для пользовательского редактора

 Этот процесс подробно описан в следующих шагах:

1. Для команд **«Сохранить** и **сохранить как»** среда использует <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службу для определения окна активного документа и, таким образом, какие элементы следует сохранить. Как только известно окно активного документа, среда находит указатель иерархии и идентификатор элементов (itemID) для документа в таблице запущенных документов. Для получения дополнительной информации [см.](../../extensibility/internals/running-document-table.md)

     Для команды «Сохранить все» среда использует информацию в таблице исходного документа для составления списка всех элементов для сохранения.

2. Когда решение получает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> вызов, оно итерируется через набор выбранных элементов (т.е. несколько вариантов, выставленных службой). <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>

3. На каждом элементе в выборе решение использует указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> иерархии для вызова метода, чтобы определить, следует ли включена команда меню «Сохранить». Если один или несколько элементов являются грязными, то включена команда Сохранить. Если иерархия использует стандартный редактор, то иерархия делегирует запрос на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> получение грязного статуса к редактору, вызывая метод.

4. На каждом выбранном элементе, который является грязным, решение <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> использует указатель иерархии для вызова метода на соответствующих иерархиях.

     В случае пользовательского редактора связь между объектом данных документа и проектом является частной. Таким образом, между этими двумя объектами обрабатываются любые особые проблемы с сохранением.

    > [!NOTE]
    > Если вы реализуете свою собственную настойчивость, не забудьте вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> метод, чтобы сэкономить время. Этот метод проверяет, чтобы убедиться, что это безопасно для сохранения файла (например, файл не читается только).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)
