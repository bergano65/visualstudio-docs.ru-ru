---
title: Настройка окна кода с помощью API прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f0b00c31280b9471da99aea55118e25dd551ad96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Настройка окна кода с помощью API прежних версий
Окно кода — объект окна документа, который поддерживает один или несколько представлений текста. Конкретные возможности окна кода зависят от службы соответствующего языка. В режиме многодокументного интерфейса (MDI) окно кода — дочерняя рамка MDI.  
  
 Управляет служб языка кода windows, и каждая языковая служба может предоставить свой собственный диспетчер окна кода. Это позволяет службе языка, добавить собственные элементы оформления в окно кода, например волнистые линии, выделение цветом и многое другое. Дополнительные сведения о том, как создать окно core см. в разделе [при создании экземпляра Core редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Окно кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта, имеющего представления текста и признаков, находящегося в объекте. При создании окна кода во время создания экземпляра ваш основной редактор службе языка можно присоединить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в окно кода, как показано на следующем рисунке.  
  
 ![График CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Окно кода  
  
 Языковая служба реализует диспетчера окон кода и отвечает за управление элементы оформления, например раскрывающуюся панель. Этот код вызывает окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> метод во время инициализации окна кода. При этом вызове языковой службы можно добавить раскрывающуюся панель или панель инструментов с кнопками (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) в окне кода.  
  
## <a name="in-this-section"></a>В этом разделе  
 `Customizing Code Windows by Using the Legacy API`  
 Описываются способы настройки windows код, с помощью предыдущих версий API.  
  
 [Как: размещения редактор в другом редакторе](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Описание для размещения второй редактор в окне редактора.  
  
 [Как: инициируют события, когда редактор теряет фокус](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Объясняется, как присоединить представления документов к объекту данных документа.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [При создании экземпляра базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)