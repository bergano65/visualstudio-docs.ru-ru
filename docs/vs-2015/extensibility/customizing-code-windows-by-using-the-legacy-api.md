---
title: Настройка кода Windows с помощью API прежних версий | Документация Майкрософт
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
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7738ef02b7f26e78197ca974fdc03b60c157799f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570248"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Настройка кода Windows с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Настройка кода Windows с помощью API прежних версий](https://docs.microsoft.com/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api).  
  
Окно кода является объектом окна документа, который поддерживает один или несколько представлений текста. Конкретные возможности окна кода зависят от соответствующего языка. В режиме многодокументного интерфейса (MDI) в окне кода является дочерняя рамка MDI.  
  
 Код windows управляются языковые службы, и каждая языковая служба может предоставить свой собственный диспетчер окон кода. Это позволяет службе языка добавлять свои собственные элементы управления в окно кода, такие как подчеркивание, выделение цветом и многое другое. Дополнительные сведения о том, как создать окно core см. в разделе [создание экземпляра Core редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Окно кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект представления текста и все элементы оформления, находящегося в объекте. При создании окна кода во время создания вашего экземпляра ядра редактора языковой службы можно присоединить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в окно кода, как показано на следующем рисунке.  
  
 ![График CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Окно кода  
  
 Языковая служба реализует диспетчер окон кода и отвечает за управление элементы оформления, например раскрывающейся панелью. Этот код вызывает окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> метод во время инициализации окна кода. При этом вызове языковой службы можно добавить раскрывающейся панелью и панелью кнопок (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) в окно кода.  
  
## <a name="in-this-section"></a>В этом разделе  
 `Customizing Code Windows by Using the Legacy API`  
 Объясняется, как настраивать код windows, с помощью предыдущих версий API.  
  
 [Практическое руководство. Размещение редактора в другом редакторе](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 В этом разделе описано размещение второй редактор внутри окна редактора.  
  
 [Практическое руководство. Инициация событий, когда редактор теряет фокус](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Объясняется, как присоединить представления документов в объект данных документа.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Создание экземпляра базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Доступ к текстовому представлению с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

