---
title: Контексты файл рабочей области в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146355"
---
# <a name="workspace-file-contexts"></a>Контексты файла рабочей области

Все подробные сведения о [открыть папку](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) рабочие области, созданные с помощью «файл контекста поставщики», реализующих <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> интерфейса. Эти расширения могут поискать в папки или файлы, чтение MSBuild файлы и файлы makefile, не сможет определить зависимости пакета, т. д. для накопления аналитики, необходимую для определения контекста файла. Контекст файла сам по себе не выполняет никаких действий, а лишь обеспечивает данные, затем можно выполнять другое расширение.

Каждый <xref:Microsoft.VisualStudio.Workspace.FileContext> имеет `Guid` связанные с ним, определяющий тип данных, он выполняет. Рабочая область использует это `Guid` позже, чтобы сопоставлять с расширениями, которые используют данные с помощью <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> свойство. Поставщик контекста файл экспортируется с метаданными, определяющий, какой контекст файла `Guid`s может привести к данных.

После определения контекста файла можно связать с любым количеством файлов или папок в рабочей области. Указанный файл или папку могут быть связаны с любым количеством контекстов файла. Это отношение многие ко многим.

Наиболее распространенных сценариев для файла контекстов, связаны с построения, отладки и языковые службы. Дополнительные сведения см. в разделе другие разделы, относящиеся к этим сценариям.

## <a name="file-context-lifecycle"></a>Жизненный цикл контекст файла

Жизненные циклы для `FileContext` недетерминированные. В любое время компонент может асинхронного запроса для некоторого набора типов контекста. Поставщики, поддерживающие некоторого подмножества типов контекста запроса будет направлен запрос. `IWorkspace` Экземпляр действует как man среднего между потребителя и поставщики через <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> метод. Потребители могут контекст запроса и краткосрочных действий на основе контекста, другие может контекст запроса и поддерживать долговременной ссылку. 

Изменения могут происходить до файлов, привести к устареванию контекста файла. Поставщик может инициировать событие на `FileContext` известить потребители обновлений. Например если контекст построения предоставляется для некоторых файлов, но изменения на диске делает недействительными этого контекста, исходный производитель можно вызвать событие. Потребителей, по-прежнему ссылается `FileContext` можно затем использовать новый `FileContext`.

>[!NOTE]
>Не предусмотрена модель принудительной для потребителей. Потребители не будут высылаться уведомления поставщика new `FileContext` после их запроса.

## <a name="expensive-file-context-computations"></a>Файл ресурсов контекста вычисления

Содержимое файла чтения с диска могут потреблять много ресурсов, особенно в том случае, если поставщик должен разрешить связь между файлами. Например поставщик может запросить контекст файла некоторые исходный файл, но контекст файла зависит от метаданных из файла проекта. При синтаксическом анализе файла проекта или оценить его с помощью MSBuild высока. Вместо этого можно экспортировать расширения `IFileScanner` для создания `FileDataValue` данных во время индексирования рабочей области. Теперь при запросе для контекстов файла `IFileContextProvider` могут быстро запрашивать индексированных данных. Дополнительные сведения об индексировании см. в разделе [индексирования рабочей](workspace-indexing.md) раздела.

>[!WARNING]
>Будьте внимательны других способов вашей `FileContext` рационально вычислений. Некоторые диалоги пользовательского интерфейса являются синхронными и полагаться на большое количество `FileContext` запросов. Примеры открытия вкладка редактора и открыв **обозревателе решений** контекстного меню. Эти действия внести много контекста построения тип запросы.

## <a name="file-context-related-apis"></a>API, связанные с контекст файла

- <xref:Microsoft.VisualStudio.Workspace.FileContext> содержит данные и метаданные.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> и <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> создания контекста файла.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Экспортирует контекст поставщика файлов.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> используется для потребителей для получения файла контекстов.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Определяет типы контекста сборки, открыть папку будет занимать.

## <a name="file-context-actions"></a>Действия контекстного файла

Хотя `FileContext` сам по себе является только данные о некоторых файлов <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> способ express и работать с этими данными. `IFileContextAction` обеспечивает высокую гибкость в его использовании. Два его наиболее распространенных случаях построения и отладки.

## <a name="reporting-progress"></a>Отчеты о ходе выполнения

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Методу передается `IProgress<IFileContextActionProgressUpdate>`, но аргумент не должен использоваться в качестве типа. `IFileContextActionProgressUpdate` является пустой интерфейс и вызову `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` может вызывать `NotImplementedException`. Вместо этого `IFileContextAction` необходимо привести аргумент в другой тип, необходимые для сценария.

Сведения о типах, предоставляемых Visual Studio см. в документации соответствующего сценария.

## <a name="file-context-action-related-apis"></a>Файл контекст действия, связанные с API-интерфейсы

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> выполняет некоторое поведение на основе `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> создает экземпляры `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> выполняется экспорт типа `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Наблюдения за файлами

Рабочая область прослушивает уведомления об изменении файлов и предоставляет <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> через <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Файлы, соответствующие параметр «ExcludedItems» не даст файл события уведомления. Порог между событиями используется для упрощения уведомления и повторяющиеся редукции. При необходимости реагировать на изменение файла, необходимо подписаться на эту службу.

>[!TIP]
>Рабочая область [службы индексирования](workspace-indexing.md) подписывается на события из файла по умолчанию. Добавление файлов и изменения вызовет применимо `IFileScanner`s событий, вызываемый для новых данных для этого файла. Удаление файлов приведет к удалению индексированных данных. Не нужно подписаться на `IFileScanner` для наблюдателя службы файлов.

## <a name="next-steps"></a>Следующие шаги

* [Индексирование](workspace-indexing.md) -индексирования рабочей собирает и сохраняет сведения о рабочей области.
* [Рабочие области](workspaces.md) -Обзор рабочей области Основные понятия и параметры хранения.
