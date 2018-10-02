---
title: Сведения о настройке элемента управления источника | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aed814ee319f9713a7b4a4c5925abcda63a04e49
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572692"
---
# <a name="source-control-configuration-details"></a>Сведения о конфигурации системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [сведения о конфигурации системы управления источника](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-configuration-details).  
  
Чтобы реализовать систему управления версиями, необходимо правильно настроить систему проектов или редактор, выполнив следующие действия:  
  
-   Запрашивать разрешение на переход на измененное состояние  
  
-   Запрашивать разрешение на сохранение файла  
  
-   Запрашивать разрешение на добавление, удаление или переименование файлов в проекте  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Запрашивать разрешение на переход на измененное состояние  
 Проект или редактора необходимо запрашивать разрешение на переход на измененное состояние ("грязный"), вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Каждый редактор, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> и получать утверждения для изменения документа из среды перед возвратом `True` для `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Проект — это редактор, для файла проекта и таким образом, несет же ответственность за реализацию отслеживания изменения состояния для файла проекта, как в текстовом редакторе, так и для ее файлов. Эти задачи выполняет среда измененное состояние решения, но необходимо обрабатывать измененное состояние любого объекта, ссылается на решение, но не хранит, таких как файл проекта или его элементов. Как правило если проект или редактор отвечает за управление сохраняемости для элемента, затем он отвечает за реализацию отслеживания изменения состояния.  
  
 В ответ на `IVsQueryEditQuerySave2::QueryEditFiles` вызова, среду можно сделать следующее:  
  
-   Отклонить вызов, чтобы изменить, в этом случае редактор или проект должны оставаться в неизмененном состоянии (чистая).  
  
-   Указывает, что данные документа требуется перезагрузка. В проекте среды будет перезагрузить данные для проекта. Редактор необходимо перезагрузить данные с диска через его <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> реализации. В любом случае контекст в проекте или в редакторе можно изменить при повторной загрузке данных.  
  
 Это сложный и трудный процесс задача модифицировать соответствующие `IVsQueryEditQuerySave2::QueryEditFiles` звонков на существующую базу кода. Таким образом эти вызовы должны интегрироваться во время создания проекта или редактора.  
  
## <a name="request-permission-to-save-a-file"></a>Запрашивать разрешение на сохранение файла  
 Прежде чем проект или редактор сохраняет файл, он должен вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Для файлов проекта эти вызовы выполняются автоматически с решения, который знает, когда следует сохранить файл проекта. Редакторы несут ответственность за обеспечение этих вызовов, если реализация редактора `IVsPersistDocData2` используется вспомогательная функция <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Если ваш редактор реализует `IVsPersistDocData2` в таким образом, то вызов `IVsQueryEditQuerySave2::QuerySaveFile` или `IVsQueryEditQuerySave2::QuerySaveFiles` выполняется автоматически.  
  
> [!NOTE]
>  Всегда выполнять эти вызовы заблаговременно — то есть во время, когда может получать отмену редактора.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Запрашивать разрешение на добавление, удаление или переименование файлов в проекте  
 Прежде чем проект можно добавить, переименовать или удалить файл или каталог, он должен вызвать соответствующий `IVsTrackProjectDocuments2::OnQuery*` метод для получения разрешения из среды. Если разрешение, то необходимо выполнить операцию и затем вызовите соответствующий проект `IVsTrackProjectDocuments2::OnAfter*` метод для уведомления среды о том, что операция завершена. Проект необходимо вызвать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс для всех файлов (например, специальные файлы) и не только родительских файлов. Файл вызовы являются обязательными, но каталог вызовы являются необязательными. Если проект содержит сведения о каталоге, то он должен вызывать соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> методы, но если он не поддерживает эти сведения, а затем среде будет выводить сведения о каталоге.  
  
 Не следует вызывать методы `IVsTrackProjectDocuments2` в проект открыть или закрыть. Прослушиватели, которые хотите эти данные во время запуска может ожидать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> событий и перебирать решение, чтобы найти необходимую им информацию. При завершении работы эта информация не требуется. `IVsTrackProjectDocuments2` предоставляется из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Для каждого add, переименование и удаление, имеется `OnQuery*` метод и `OnAfter*` метод. Вызовите `OnQuery*` метода, чтобы запросить разрешение на добавление, переименование или удаление файла или каталога. Вызовите `OnAfter*` метод после того как файл или каталог, были добавлены, переименованы или удалены, и состояние проекта отражает новое состояние.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)

