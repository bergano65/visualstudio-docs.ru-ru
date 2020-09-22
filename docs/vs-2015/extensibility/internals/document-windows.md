---
title: Окна документов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842532"
---
# <a name="document-windows"></a>Окна документов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В Visual Studio *окно документа* является дочерним окном с фреймами, связанным с окном многодокументного интерфейса (MDI). Окна документов обычно используются для просмотра и изменения исходного кода или текста, но они также могут содержать другие функциональные типы. Окна документов:  
  
- Можно организовать в отдельные группы горизонтальных или вертикальных вкладок в родительском интерфейсе MDI, чтобы одновременно просматривать несколько файлов.  
  
- Может закрепляться в любом порядке в родительском интерфейсе MDI.  
  
- Может быть свободно плавающей.  
  
- Связаны в порядке табуляции с другими окнами MDI.  
  
  Команды для группирования, закрепления и плавающего типа можно найти в контекстном меню на вкладке окна документа.  
  
  Дополнительные сведения о поведении окон в Visual Studio см. в разделе [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Реализация окна документа  
 Окна документов создаются путем реализации редактора. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Интерфейс создает окна документов в процессе создания экземпляра редактора. Дополнительные сведения см. [в разделе устаревшие интерфейсы в редакторе](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Чтобы обеспечить обратную и прямую точку навигации в окне, реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> интерфейс. Текстовый редактор использует текстовые маркеры для обнаружения точек перехода в документе.  
  
## <a name="the-running-document-table"></a>Таблица выполняющегося документа  
 Интегрированная среда разработки использует таблицу выполняемых документов (РДТ) для наблюдения за состоянием каждого окна документа. РДТ — это механизм, с помощью которого окна документов получают уведомления о событиях, например о закрытии решения или изменении файла. Дополнительные сведения см. в разделе [выполнение таблицы документов](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>См. также:  
 [Отложенная загрузка документов](../../extensibility/internals/delayed-document-loading.md)
