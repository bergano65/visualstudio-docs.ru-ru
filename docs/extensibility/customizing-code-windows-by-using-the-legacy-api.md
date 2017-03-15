---
title: "Настройка кода Windows с помощью API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - кода windows"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Настройка кода Windows с помощью API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Окно кода — объект окна документа, которая поддерживает один или несколько текстовых представлений. Конкретные возможности окна кода зависят от службы соответствующего языка. В режиме многодокументного интерфейса \(MDI\) окно кода имеет дочерние окна MDI.  
  
 Код windows управляются языковые службы и служба каждого языка программирования можно предоставить свой собственный код диспетчера окон. Это позволяет службе языка добавить свои собственные элементы оформления окна кода, такие как подчеркивание, выделение цветом и многое другое. Дополнительные сведения о том, как создать окно ядра в разделе [Создание базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Окно кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекта, имеющего представления текста и признаков, находящегося в объекте. При создании окна кода во время вашего экземпляра основной редактор языка службы можно присоединить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в окно кода, как показано на следующем рисунке.  
  
 ![График CodeWindow](../extensibility/media/vscodewindow.png "vscodewindow")  
Окно кода  
  
 Языковая служба реализует диспетчер окон кода и отвечает за управление элементы оформления, например раскрывающуюся панель. Этот код вызывает окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> метод во время инициализации окна кода. При этом вызове языковую службу можно добавить раскрывающуюся панель или панель инструментов с кнопками \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) в окне кода.  
  
## Содержание  
 `Customizing Code Windows by Using the Legacy API`  
 Объясняется, как настраивать код windows, с помощью API прежних версий.  
  
 [Практическое руководство: размещения редактора в другом редакторе](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Объясняет, как разместить второй редактор в окно редактора.  
  
 [Практическое руководство: инициируют события, когда редактор фокус.](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Объясняет, как присоединить представления документа в объект данных документа.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Создание базового редактора с помощью API прежних версий](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Доступ к theText представление с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)