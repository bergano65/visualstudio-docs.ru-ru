---
title: Окна документов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708517"
---
# <a name="document-windows"></a>Окна документов
В Visual Studio *окно документа* представляет собой окно в рамке, связанное с многодокументным интерфейсом (MDI). Окна документов обычно используются для отображения и модификации исходного кода или текста, но они также могут размещать другие функциональные типы. Окна документов:

- Может быть организована в отдельных горизонтальных или вертикальных групп вкладок в родительском MDI, так что несколько файлов могут быть просмотрены в то же время.

- Может быть пристыкован в любом порядке в родительском MDI.

- Можно свободно плавать.

- Связаны в порядке вкладки с другими окнами MDI.

  Команды для группировки, стыковки и плавания можно найти в меню ярлыка для вкладки окна документа.

  Для получения дополнительной [информации](../../ide/customizing-window-layouts-in-visual-studio.md)о поведении окон в Visual Studio см.

## <a name="document-window-implementation"></a>Реализация окна документов
 Окна документов создаются путем реализации редактора. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> создает окна документов как часть мгновенного редактора. Для получения дополнительной информации смотрите [интерфейсы Legacy в редакторе](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Чтобы обеспечить обратные и передние <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> точки навигации в окне, реализуем интерфейс. Текстовый редактор использует текстовые маркеры для определения точек навигации в документе.

## <a name="the-running-document-table"></a>Таблица документов «Бегущий»
 IDE использует таблицу документов Running (RDT) для отслеживания состояния каждого окна документа. RDT — это механизм, с помощью которого окна документов уведомляются о событиях, например, при закрытии решения или при редактировании файла. Для получения дополнительной информации [см.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>См. также
- [Задержка загрузки документов](../../extensibility/internals/delayed-document-loading.md)
