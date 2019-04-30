---
title: Объект VSCodeWindow | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b1a3c19d349b84b10e0f36aca57a24aaac0d521
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953131"
---
# <a name="vscodewindow-object"></a>Объект VSCodeWindow
Окно кода — это окно специализированные документов, который может включать одно или несколько представлений текста, обычно <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.

 С точки зрения архитектуры окно кода — это окно документов, который находится в пределах фрейма окна. С функциональной точки зрения окно кода — просто это окно документов с помощью дополнительных функций. В режиме многодокументного интерфейса (MDI) в окне кода является дочерняя рамка MDI. Дополнительные сведения см. в разделе [Настройка кода windows, используя старый API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).

 В следующей таблице приведены интерфейсы <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> объекта.

|Метод|Описание|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный доступ механизм для поиска службы, определяющий глобальный уникальный идентификатор (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет несколько дочерних интерфейса (MDI) документа, содержащий одно или несколько представлений кода.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)