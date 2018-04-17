---
title: Настройка окна кода с помощью API прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8284985003415ef3e723fe735e64481c3666180a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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