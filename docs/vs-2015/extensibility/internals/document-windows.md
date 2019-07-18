---
title: Документирование Windows | Документация Майкрософт
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436336"
---
# <a name="document-windows"></a>Окна документов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В Visual Studio *окно документа* — рамке дочернее окно, связанный с окном многодокументного интерфейса (MDI). Окна документов обычно используются для отображения и изменения исходного кода или текста, но они также можно размещать другие функциональные типы. Окна документов:  
  
- Можно организовывать в отдельной вкладке горизонтальную или вертикальную групп в родительской MDI, в то же время можно просматривать несколько файлов.  
  
- Можно закрепить в любом порядке, в родительской MDI.  
  
- Может быть свободно перемещается.  
  
- Связаны в последовательности табуляции равным других окон интерфейса MDI.  
  
  Команды для группирования, закрепленные и плавающие находятся в контекстном меню для вкладки окна документа.  
  
  Дополнительные сведения о поведением окна в Visual Studio, см. в разделе [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Реализация окна документа  
 Окна документов создаются путем реализации редактора. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Интерфейс создает окна документов в процессе создания экземпляра редактора. Дополнительные сведения см. в разделе [прежних версий интерфейсов в редакторе](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
> Для предоставления назад и вперед точки навигации в окне, реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> интерфейс. Текстовый редактор использует маркеры текста для определения точки навигации в документе.  
  
## <a name="the-running-document-table"></a>Запуск таблицы документов  
 Интегрированная среда разработки использует таблице выполняющихся документов (RDT) для отслеживания состояния каждого окна документа. RDT — это механизм, посредством документа, который windows уведомляются об события, например при закрытии решения или после редактирования файла. Дополнительные сведения см. в разделе [таблице выполняющихся документов](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>См. также  
 [Отложенная загрузка документов](../../extensibility/internals/delayed-document-loading.md)
