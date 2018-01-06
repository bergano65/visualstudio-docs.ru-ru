---
title: "Окна документов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Окна документов
В Visual Studio *окно документа* является рамке дочернего окна, связанный с помощью окна многодокументного интерфейса (MDI). Окна документов обычно используются для отображения и изменения исходного кода или текста, но они может также содержать другие функциональные типы. Окна документов:  
  
-   Могут быть организованы в отдельной вкладке горизонтальной или вертикальной групп в родительской MDI-приложения, одновременно можно просматривать несколько файлов.  
  
-   Можно закрепить в любом порядке в родительской MDI-приложения.  
  
-   Может быть свободно перемещается.  
  
-   Связаны в последовательности табуляции для других окон MDI.  
  
 Команды для группирования, закрепленные и плавающие находятся в контекстном меню для вкладки окна документа.  
  
 Дополнительные сведения о поведении окна в Visual Studio см. в разделе [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Реализация окно документа  
 Окна документов создаются путем реализации редактора. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Интерфейс создает окон документов в процессе создания экземпляра редактора. Дополнительные сведения см. в разделе [интерфейсы прежних версий в редакторе](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Для предоставления назад и вперед точки навигации в окне, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> интерфейса. Текстовый редактор использует маркеры текст для определения точки навигации в документе.  
  
## <a name="the-running-document-table"></a>В таблице документа запущена  
 Интегрированная среда разработки использует запуска таблицы документов (RDT) для отслеживания состояния каждого окна документа. RDT — это механизм, через какой документ уведомляются windows событий, например при закрытии решения или после редактирования файла. Дополнительные сведения см. в разделе [под управлением таблицы Document](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>См. также  
 [Отложенная загрузка документов](../../extensibility/internals/delayed-document-loading.md)