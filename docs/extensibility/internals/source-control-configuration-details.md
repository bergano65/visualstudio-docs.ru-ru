---
title: Детали конфигурации управления исходом (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705283"
---
# <a name="source-control-configuration-details"></a>Сведения о конфигурации системы управления версиями
Для реализации элемента управления исходным источником необходимо правильно настроить проектную систему или редактор, чтобы сделать следующее:

- Запрос разрешения на переход в измененное состояние

- Запрос разрешения на сохранение файла

- Запрос разрешения на добавление, удаление или переименование файлов в проекте

## <a name="request-permission-to-transition-to-changed-state"></a>Запрос разрешения на переход в измененное состояние
 Проект или редактор должны запросить разрешение на переход к <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>измененному (грязному) состоянию, позвонив. Каждый редактор, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> который <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> реализует должны вызвать и получить `True` одобрение, чтобы изменить документ из среды, прежде чем вернуться на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Проект по существу является редактором файла проекта и, как следствие, несет такую же ответственность за реализацию отслеживания измененного состояния для файла проекта, как и текстовый редактор для его файлов. Среда обрабатывает измененное состояние решения, но необходимо обрабатывать измененное состояние любого объекта, на который ссылается решение, но не хранит, например файл проекта или его элементы. Как правило, если ваш проект или редактор отвечает за управление сохранением элемента, то он отвечает за реализацию отслеживания измененного состояния.

 В ответ `IVsQueryEditQuerySave2::QueryEditFiles` на вызов окружающая среда может сделать следующее:

- Отклонить призыв к изменению, и в этом случае редактор или проект должны оставаться в неизменном (чистом) состоянии.

- Укажите, что данные документа должны быть перезагружены. Для проекта среда перезагрузит данные для проекта. Редактор должен перезагрузить данные с <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> диска через его реализацию. В любом случае контекст в проекте или редакторе может изменяться при перезагрузке данных.

  Это сложная и трудная задача `IVsQueryEditQuerySave2::QueryEditFiles` по переоборудованию соответствующих вызовов на существующую базу кода. В результате эти вызовы должны быть интегрированы при создании проекта или редактора.

## <a name="request-permission-to-save-a-file"></a>Запрос Разрешения на сохранение файла
 Перед тем, как проект или редактор <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> сохраняет <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>файл, он должен вызвать или . Для файлов проекта эти вызовы автоматически выполняются решением, которое знает, когда нужно сохранить файл проекта. Редакторы несут ответственность за выполнение этих `IVsPersistDocData2` вызовов, если <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>редактор реализации использует функцию помощника . Если ваш редактор `IVsPersistDocData2` реализует таким образом, `IVsQueryEditQuerySave2::QuerySaveFile` то `IVsQueryEditQuerySave2::QuerySaveFiles` вызов или для вас.

> [!NOTE]
> Всегда делайте эти вызовы упреждаю, то есть в то время, когда ваш редактор может получить отмену.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Запрос разрешения на добавление, удаление или переименование файлов в проекте
 Прежде чем проект может добавить, переименовать или удалить файл или `IVsTrackProjectDocuments2::OnQuery*` каталог, он должен вызвать соответствующий метод, чтобы запросить разрешение от среды. Если разрешение получено, проект должен завершить операцию, `IVsTrackProjectDocuments2::OnAfter*` а затем вызвать соответствующий метод, чтобы уведомить среду о завершении операции. Проект должен вызывать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейса для всех файлов (например, специальные файлы), а не только родительские файлы. Вызовы файлов являются обязательными, но вызовы каталога не являются обязательными. Если ваш проект имеет информацию каталога, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> то он должен вызвать соответствующие методы, но если он не имеет этой информации, то среда будет делать вывод ы информации каталога.

 Проект не должен называть методы `IVsTrackProjectDocuments2` проекта открытыми или близкими. Слушатели, которые хотят получить эту <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> информацию в стартапе, могут дождаться события и итерировать решение, чтобы найти нужную им информацию. При выключении эта информация не требуется. `IVsTrackProjectDocuments2`предоставляется из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Для каждого добавления, переименования и `OnQuery*` удаления `OnAfter*` действия существует метод и метод. Вызов `OnQuery*` испросите метод, чтобы запросить разрешение на добавление, переименование или удаление файла или каталога. Вызов `OnAfter*` метода после добавления, переименования или удаления файла после добавления, переименования или удаления, а состояние проекта отражает новое состояние.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
