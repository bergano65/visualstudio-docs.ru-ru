---
title: "Сведения о настройке управления источника | Microsoft Docs"
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
  - "Система управления версиями [Visual Studio SDK], сведения о конфигурации"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Сведения о настройке управления источника
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Для реализации системы управления версиями, необходимо правильно настроить систему или редактор проекта, чтобы выполнить следующие действия:  
  
-   Разрешение запроса к переходу в состояние измененных  
  
-   Разрешение запроса сохранить файл  
  
-   Запросить разрешение на добавление, удаление и переименование файлов в проекте  
  
## Запрос разрешения для перехода в состояние измененных  
 Проект должен запросить разрешение или редактор для перехода измененному \(состояние путем вызова пакостному\) <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>.  Каждый редактор, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> вызов  `True` и получите утверждение, чтобы изменить документ из среды перед возвращением  `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`для  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> .  Проект по существу редактор для файла проекта, и в результате имеет ту же изменить\-состояние для реализации отвечает за отслеживание для файла проекта как текстовый редактор для ее файлов.  Дескрипторы среды измененное состояние решения, но необходимо обработать измененное состояние любого объекта ссылки решения, но не сохраняется, например файл проекта или его элементы.  Как правило, если проект или редактор отвечают за управление сохраняемости для элемента, она отвечает за отслеживание изменить\-состояния реализации.  
  
 в ответ на `IVsQueryEditQuerySave2::QueryEditFiles` вызов среда может выполнить следующие действия:  
  
-   Отклонить вызов, чтобы изменить, и в этом случае редактор или проект, должны оставаться в неизменном состоянии \(пустую\).  
  
-   Показать, что данные документа должны быть перезапускаются.  Для проекта среда перезапускает данных для проекта.  Редактор должен перезапустить данных с диска посредством своего <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> реализация.  В любом случае контекст в проекте или редактор могут меняться, когда данные перезапускаются.  
  
 Сложная и жесткой задача retrofit соответствующее `IVsQueryEditQuerySave2::QueryEditFiles` вызовы в существующую базу кода.  В результате эти вызовы должны быть встроены в процессе создания проекта или редактора.  
  
## Разрешение запроса сохранить файл  
 Перед этим проектом или редактором сохраняет файл, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>OR  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> .  Для файлов проекта, эти вызовы автоматически завершены решением, который знает, когда сохранить файл проекта.  Редакторы отвечают за вызовом этих если реализация редактора <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>использует вспомогательную функцию  `IVsPersistDocData2` .  Если пользовательский редактор реализует `IVsPersistDocData2` таким образом, после чего вызов  `IVsQueryEditQuerySave2::QuerySaveFile` OR  `IVsQueryEditQuerySave2::QuerySaveFiles` делает.  
  
> [!NOTE]
>  Всегда вызова этих preemptively\-что, синхронно с редактор может получить отменить.  
  
## Запросить разрешение на добавление, удаление и переименование файлов в проекте  
 Перед построением проекта может добавлять, переименовать или удалить файл или каталог, он должен вызывать соответствующий `IVsTrackProjectDocuments2::OnQuery*` метод, чтобы запросить разрешение из среды.  Если предоставлено разрешение, он должен выполнить операцию а затем вызвать соответствующий `IVsTrackProjectDocuments2::OnAfter*` метод для уведомления среды, что операция завершена.  Проект должен вызвать методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс для всех файлов \(например, специальные файлов\), а не просто родительских файлов.  Вызовы файла не требуются, но вызовы каталога являются необязательными.  Если проект содержит сведения о каталоге, то он должен вызывать соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> методы, но, если он не содержит этих сведений среда вывести данные каталога.  
  
 Проект не должен вызывать методы `IVsTrackProjectDocuments2` при открытии или конце проекта.  Прослушиватели, которые хотят это сведения о запуске могут ожидать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> событие и выполняет итерацию решение для поиска сведений ним.  При завершении работы, эти сведения не требуется.  `IVsTrackProjectDocuments2` предоставляет из  <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Для каждого добавьте, переименование и удаление действие `OnQuery*` метод и  `OnAfter*` метод.  Вызовите `OnQuery*` метод, чтобы запросить разрешение на добавление, переименование или удаление файла или каталога.  Вызовите `OnAfter*` был добавлен метод после файла или каталога, переименованы или удалено и состояние проекта автоматически устанавливает новое состояние.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)