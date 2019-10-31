---
title: Объект Вскодевиндов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189051"
---
# <a name="vscodewindow-object"></a>Объект Вскодевиндов
Окно кода — это специализированное окно документа, которое может содержать одно или несколько текстовых представлений, обычно <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объект.

 В архитектуре окно кода — это окно документа, которое находится в рамке окна. Функционально окно кода — это просто окно документа с дополнительными функциями. В режиме многодокументного интерфейса (MDI) окно кода является дочерним фреймом MDI. Дополнительные сведения см. [в разделе Настройка окон кода с помощью API прежних версий](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 В следующей таблице содержатся интерфейсы в объекте <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>.

|Метод|Описание|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Предоставляет универсальный механизм доступа для определения службы, которая идентифицируется глобальным уникальным идентификатором (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет дочерний интерфейс многодокументного интерфейса (MDI), содержащий одно или несколько представлений кода.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет рамку окна.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)