---
title: Контексты файла рабочей области в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 93690eab989cee62d756a774675bf1d46da017fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826868"
---
# <a name="workspace-file-contexts"></a>Контексты файла рабочей области

Вся аналитика в [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) рабочие области создаются «контекста поставщики файлов», которые реализуют <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> интерфейс. Эти расширения могут найти шаблоны в папки или файлы, прочитайте MSBuild и файлы makefile, обнаружить зависимости пакетов, т. д. для накопления insights, необходимую для определения контекста файла. Контекст файла сам по себе не выполняет никаких действий, а лишь обеспечивает данных, которую другое расширение может затем.

Каждый <xref:Microsoft.VisualStudio.Workspace.FileContext> имеет `Guid` связанные с ней, определяющий тип данных, он выполняет. Рабочая область использует этот `Guid` позже, чтобы сопоставить его с расширениями, которые используют данные с помощью <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> свойство. Контекст поставщика файлов экспортируется с помощью метаданных, определяющий, какой контекст файла `Guid`s может привести к данные.

После определения контекста файла можно связать с любым количеством файлов или папок в рабочей области. Заданного файла или папки могут быть связаны с любым количеством контексты файла. Это отношение многие ко многим.

Наиболее распространенных сценариев для файла контекстов, связаны с построения, отладки и языковых служб. Дополнительные сведения см. в разделе подразделы, касающиеся этих сценариев.

## <a name="file-context-lifecycle"></a>Жизненный цикл контекст файла

Жизненные циклы для `FileContext` недетерминированные. В любое время компонент асинхронно выполнить запрос для некоторый набор типов контекста. Поставщики, поддерживающие некоторого подмножества типов контекста запроса будет направлен запрос. `IWorkspace` Выступает в качестве посредника между потребителей и поставщиков через <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> метод. Потребители могут контекст запроса и краткосрочных действий на основе контекста, а другие пользователи могут запросить контекст и управлять долгоживущие ссылку. 

Файлы, которые вызывают контекста файла к устареванию может внесения изменений. Поставщик может инициировать событие на `FileContext` для уведомления потребителей обновлений. Например если контекст сборки предоставляется для некоторых файлов, но на диске изменение приведет к недопустимости этого контекста, исходный производитель могут вызывать событие. По-прежнему ссылаясь на него потребителей `FileContext` можно затем использовать для нового `FileContext`.

>[!NOTE]
>Не существует модели Push-уведомлений для потребителей. Пользователи не будут высылаться уведомления поставщика new `FileContext` после их запроса.

## <a name="expensive-file-context-computations"></a>Дорогостоящие файл контекст вычислений

Содержимое файла чтения с диска может быть дорогостоящим, особенно в том случае, если поставщик должен разрешить связь между файлами. Например поставщик может запрашиваться для контекста файла некоторые исходный файл, но контекст файла зависит от метаданных из файла проекта. Синтаксический анализ файла проекта или его оценку с помощью MSBuild является дорогостоящим. Вместо этого можно экспортировать расширение `IFileScanner` для создания `FileDataValue` данных во время индексирования рабочей области. Теперь при запросе контексты файла `IFileContextProvider` могут быстро запрашивать для индексированных данных. Дополнительные сведения об индексировании см. в разделе [индексирования рабочей области](workspace-indexing.md) раздела.

>[!WARNING]
>Будьте осторожны при других способов вашей `FileContext` может потреблять много ресурсов для вычисления. Некоторые взаимодействия пользовательского интерфейса являются синхронными и полагаться на большое количество `FileContext` запросов. Примеры, открыв вкладку редактора и открыв **обозревателе решений** контекстного меню. Эти действия сделать много контекст сборки введите запросов.

## <a name="file-context-related-apis"></a>API, связанные с контекста файла

- <xref:Microsoft.VisualStudio.Workspace.FileContext> содержит данные и метаданные.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> и <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> создать контекст файла.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Экспортирует контекст поставщика файлов.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> используется для потребителей для получения файла контекстов.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Определяет типы контекста сборки, в которых используется открыть папку.

## <a name="file-context-actions"></a>Файл контекстные действия

Хотя `FileContext` сам представляют собой просто данные о некоторые файлы <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> — это способ express и выполнять с ними. `IFileContextAction` отличается гибкостью в его использования. Два из его наиболее распространенных случаев построения и отладки.

## <a name="reporting-progress"></a>Отчеты о ходе выполнения

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Методу передается `IProgress<IFileContextActionProgressUpdate>`, но аргумент не должен использоваться в качестве типа. `IFileContextActionProgressUpdate` Это пустой интерфейс и вызов `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` может выдавать `NotImplementedException`. Вместо этого `IFileContextAction` необходимо привести аргумент в другой тип, необходимые для сценария.

Сведения о типах, предоставляемых Visual Studio см. в разделе документации соответствующего сценария.

## <a name="file-context-action-related-apis"></a>API, связанные с действие в контексте файла

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> выполняет некоторое поведение на основе `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> создает экземпляры `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> выполняется экспорт типа `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Наблюдения за файлами

Прослушивает уведомления об изменении файла рабочей области и предоставляет <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> через <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Файлы, соответствует значению «ExcludedItems» не будет создавать файл события уведомления. Для упрощения уведомлений и повторяющиеся сокращения используется пороговое значение между событиями. Когда необходимо реагировать на изменение файла, вы должны подписаться на эту службу.

>[!TIP]
>Рабочая область [службой индексирования](workspace-indexing.md) подписывается на события файла по умолчанию. Добавление файла и изменение файлов приведет к соответствующей `IFileScanner`s событий, вызываемый для новых данных для этого файла. Удаление файлов приведет к удалению индексированных данных. Не нужно подписаться на `IFileScanner` в службу инспектор файлов.

## <a name="next-steps"></a>Следующие шаги

* [Индексирование](workspace-indexing.md) -индексирования рабочей области собирает и сохраняет сведения о рабочем пространстве.
* [Рабочие области](workspaces.md) -просмотрите основные понятия рабочей области и параметры хранения.
