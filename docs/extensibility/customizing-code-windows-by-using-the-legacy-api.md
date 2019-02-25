---
title: Настройка кода Windows с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0ea617a252d60d8e8d5810c42f7331508c28165
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708983"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Настраивать код windows с помощью предыдущих версий API
Окно кода является объектом окна документа, который поддерживает один или несколько представлений текста. Конкретные возможности окна кода зависят от соответствующего языка. В режиме многодокументного интерфейса (MDI) в окне кода является дочерняя рамка MDI.

 Код windows управляются языковые службы, и каждая языковая служба может предоставить свой собственный диспетчер окон кода. Это позволяет службе языка добавлять свои собственные элементы управления в окно кода, такие как подчеркивание, выделение цветом и многое другое. Дополнительные сведения о том, как создать окно core см. в разделе [экземпляра базового редактора с помощью старый API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).

 Окно кода <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект представления текста и все элементы оформления, находящегося в объекте. При создании окна кода во время создания вашего экземпляра ядра редактора языковой службы можно присоединить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> в окно кода, как показано на следующем рисунке.

 ![График CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow") окно кода

 Языковая служба реализует диспетчер окон кода и отвечает за управление элементы оформления, например раскрывающейся панелью. Этот код вызывает окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> метод во время инициализации окна кода. При этом вызове языковой службы можно добавить раскрывающейся панелью и панелью кнопок (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) в окно кода.

## <a name="in-this-section"></a>Содержание раздела
 `Customizing Code Windows by Using the Legacy API` Объясняется, как настраивать код windows, с помощью предыдущих версий API.

- [Практическое руководство. Размещение в другом редакторе редактор](../extensibility/how-to-host-an-editor-in-another-editor.md) описано размещение второй редактор внутри окна редактора.

- [Практическое руководство. Инициируют события, когда редактор теряет фокус](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md) объясняется, как присоединить представления документов в объект данных документа.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Создать экземпляр базового редактора с помощью предыдущих версий API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
- [Представление theText доступ с помощью предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)