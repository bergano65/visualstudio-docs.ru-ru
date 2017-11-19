---
title: "Сведения о настройке элемента управления источника | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17e14d4f8d3d62297ae1d2f3e62a9ed0574fef9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-configuration-details"></a>Сведения о конфигурации исходного элемента управления
Для реализации системы управления версиями, необходимо правильно настроить систему проектов или редактор, чтобы сделать следующее:  
  
-   Запрашивать разрешение на переход на измененное состояние  
  
-   Запрашивать разрешение на сохранение файла  
  
-   Запрашивать разрешение на добавление, удаление или переименование файлов в проекте  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Запрашивать разрешение на переход на измененное состояние  
 Проект или редактора необходимо запрашивать разрешение на переход на измененное состояние («грязные») путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Каждый редактор, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и получать утверждения для изменения документа из среды перед возвратом `True` для `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Проект — редактор, к файлу проекта и в результате несет ответственность за же по реализации отслеживания изменения состояния для файла проекта, как для файлов в текстовом редакторе. Среде обрабатывает измененное состояние решения, но необходимо обработать измененное состояние любого объекта ссылается на решение, но не сохраняет как файл проекта или его элементов. Как правило если проект или редактор отвечает за управление сохраняемости для элемента, будет отвечать за реализацию отслеживания изменения состояния.  
  
 В ответ на `IVsQueryEditQuerySave2::QueryEditFiles` вызвать, среде можно выполнять следующие задачи:  
  
-   Отклонить вызов для изменения, в этом случае редактор или проект должен оставаться в неизмененном состоянии (чистая).  
  
-   Укажите, следует повторно загрузить данные документа. В проекте среды будет перезагрузить данные для проекта. Редактор необходимо перезагрузить данные с диска через его <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> реализации. В любом случае контекст в проекте или в редакторе можно изменить при повторной загрузке данных.  
  
 Это задача сложна и затруднительна модифицировать соответствующие `IVsQueryEditQuerySave2::QueryEditFiles` звонков на существующую базу кода. В результате во время создания проекта или редактора необходимо интегрировать эти вызовы.  
  
## <a name="request-permission-to-save-a-file"></a>Запрашивать разрешение на сохранение файла  
 Прежде чем проект или редактор сохраняет файл, он должен вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Для файлов проекта эти вызовы выполняются автоматически с решения, которое знает, когда следует сохранить файл проекта. Редакторы отвечают за эти вызовы, если реализация редактора `IVsPersistDocData2` использует вспомогательную функцию <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Если ваш редактор реализует `IVsPersistDocData2` таким образом, а затем вызов `IVsQueryEditQuerySave2::QuerySaveFile` или `IVsQueryEditQuerySave2::QuerySaveFiles` специально для вас.  
  
> [!NOTE]
>  Всегда выполнять эти вызовы предварительно — то есть, во время, когда ваш редактор будет получать "Отмена".  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Запрашивать разрешение на добавление, удаление или переименование файлов в проекте  
 Прежде чем проект можно добавить, переименовать или удалить файл или каталог, он должен вызвать соответствующий `IVsTrackProjectDocuments2::OnQuery*` метод для получения разрешения из среды. Если предоставлено разрешение, то необходимо выполнить операцию и затем вызовите соответствующий проект `IVsTrackProjectDocuments2::OnAfter*` метод для уведомления среды, что операция завершена. Проект необходимо вызывать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс для всех файлов (например, файлов со специальным) и не только для родительских файлов. Файл вызовы являются обязательными, но каталог вызовы являются необязательными. Если проект содержит сведения о каталоге, то он должен вызывать соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> методы, но если он не имеет эти сведения, то среды выведет сведения о каталоге.  
  
 Не следует вызывать методы `IVsTrackProjectDocuments2` в проект можно открыть или закрыть. Прослушивателей, которые хотите эти сведения во время запуска может ожидать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> событий и прохода решение, чтобы найти сведения, которые нужны. При завершении работы эта информация не требуется. `IVsTrackProjectDocuments2`предоставляется из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Для каждого add, переименование и удаление — `OnQuery*` метод и `OnAfter*` метод. Вызовите `OnQuery*` метод, чтобы запросить разрешение на добавление, переименование или удаление файла или каталога. Вызовите `OnAfter*` метод после файл или каталог были добавлены, переименован или удален, и состояние проекта отражает новое состояние.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)