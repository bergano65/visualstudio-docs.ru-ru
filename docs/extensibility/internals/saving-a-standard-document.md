---
title: Сохранение стандартного документа | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724097"
---
# <a name="saving-a-standard-document"></a>Сохранение стандартного документа
Среда обрабатывает команды Сохранить, сохранить как и сохранить все. Когда пользователь выбирает команду **сохранить**, **Сохранить как**или **сохранить все** из меню **файл** или закрывает **решение, в**результате чего выполняется следующий процесс.

 ![Стандартный редактор](../../extensibility/internals/media/public.gif "Public") Сохранение, сохранение как и сохранение всей обработки команд для стандартного редактора

 Этот процесс описан в следующих шагах.

1. Если выбраны команды **сохранить** и **Сохранить как** , среда использует службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> для определения активного окна документа и, таким образом, элементы, которые следует сохранить. Когда окно активного документа будет известно, среда находит указатель иерархии и идентификатор элемента (itemID) для документа в выполняемой таблице документов. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).

    Если выбрана команда **сохранить все** , среда использует сведения из таблицы «выполняемый документ» для компиляции списка всех элементов для сохранения.

2. Когда решение получает вызов <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>, оно выполняет итерацию по набору выбранных элементов (то есть множественный выбор, предоставленный службой <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>).

3. В каждом выбранном элементе решение использует указатель иерархии для вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>, чтобы определить, должна ли быть включена команда меню " **сохранить** ". Если один или несколько элементов являются "грязными", команда " **сохранить** " будет включена. Если в иерархии используется стандартный редактор, то иерархия делегирует запрос о состоянии "грязного" в редактор, вызывая метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>.

4. Для каждого выбранного элемента, который является "грязным", решение использует указатель иерархии для вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> в соответствующих иерархиях.

    Обычно в иерархии для редактирования документа используется стандартный редактор. В этом случае объект данных документа для этого редактора должен поддерживать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>. После получения вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> проект должен сообщить редактору, что документ сохраняется, вызвав метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> для объекта данных документа. Редактор может разрешить среде обработку диалогового окна " **Сохранить как** ", вызвав `Query Service` для интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>. Он возвращает указатель на интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>. Затем редактор должен вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>, передавая указатель на реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> в редакторе с помощью параметра `pPersistFile`. Затем среда выполняет операцию сохранения и предоставляет диалоговое окно « **Сохранить как** » для редактора. Затем среда обращается к редактору с <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.

5. Если пользователь пытается сохранить документ без заголовка (то есть ранее несохраненный документ), то выполняется команда Сохранить как.

6. Для команды "Сохранить как" среда отображает диалоговое окно Сохранить как, предлагающее пользователю ввести имя файла.

    Если имя файла изменилось, то иерархия отвечает за обновление кэшированных данных фрейма документа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument).

   Если команда **Сохранить как** перемещает расположение документа, а иерархия чувствительна к расположению документа, то иерархия отвечает за передачу владения открытым окном документа в другую иерархию. Например, это происходит, если проект отслеживает, является ли файл внутренним или внешним файлом (прочим файлом) относительно проекта. Используйте следующую процедуру, чтобы изменить принадлежность файла к проекту прочих файлов.

## <a name="changing-file-ownership"></a>Изменение владельца файла

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Изменение владельца файла на проект прочих файлов

1. Служба запросов для интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>.

     Возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2>.

2. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`), чтобы переместить документ в новую иерархию. Иерархия, выполняющая команду "Сохранить как", вызывает этот метод.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)