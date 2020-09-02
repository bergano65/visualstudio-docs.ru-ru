---
title: Настройка окон кода с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556143"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Настройка кода Windows с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно кода — это объект окна документа, поддерживающий одно или несколько текстовых представлений. Конкретные функции окна кода зависят от службы, соответствующей языку. В режиме многодокументного интерфейса (MDI) окно кода является дочерним фреймом MDI.  
  
 Окна кода управляются языками служб, и каждая языковая служба может предоставлять собственный диспетчер окон кода. Это позволяет языковой службе добавлять собственные элементы оформления в окно кода, такие как волнистые линии, Цветовая раскраска и т. д. Дополнительные сведения о создании основного окна см. в статье Создание [базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Окно кода — это <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект, имеющий текстовое представление и все декоративные элементы, расположенные в объекте. При создании окна кода во время создания экземпляра базового редактора языковая служба может подключить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> к окну кода, как показано на следующем рисунке.  
  
 ![График CodeWindow](../extensibility/media/vscodewindow.gif "вскодевиндов")  
Окно кода  
  
 Языковая служба реализует диспетчер окон кода и отвечает за управление декоративными элементами, такими как раскрывающиеся полосы. Окно кода вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> метод во время инициализации окна кода. Когда этот вызов сделан, языковая служба может добавить раскрывающийся список или панель кнопок ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) в окно кода.  
  
## <a name="in-this-section"></a>в этом разделе  
 `Customizing Code Windows by Using the Legacy API`  
 Объясняет, как настроить окна кода с помощью API прежних версий.  
  
 [Практическое руководство. Размещение редактора в другом редакторе](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Описание размещения второго редактора в окне редактора.  
  
 [Практическое руководство. Инициация событий, когда редактор теряет фокус](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Объясняет, как присоединить представление документа к объекту данных документа.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Создание экземпляра базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
