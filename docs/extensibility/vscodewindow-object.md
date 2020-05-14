---
title: Объект VSCodeWindow Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697960"
---
# <a name="vscodewindow-object"></a>Объект VSCodeWindow
Окно кода — это специализированное окно документа, которое <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> может включать одно или несколько текстовых представлений, обычно объект.

 Архитектурно окно кода — это окно документа, напавще е-в оконной раме. Функционально окно кода является просто окном документа с дополнительными функциями. В режиме интерфейса с несколькими документами (MDI) окно кода представляет собой детскую рамку MDI. Для получения дополнительной [информации см. Настройка кодовых окон с помощью устаревшего API.](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)

 Следующая таблица включает интерфейсы объекта. <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>

|Метод|Описание|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Обеспечивает общий механизм доступа для поиска службы, которую идентифицирует глобально уникальный идентификатор (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Представляет собой многократный интерфейс документа (MDI), содержащий одно или несколько представлений кода.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Заполняет оконную раму.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Цифры отодвите](https://www.microsoft.com/download/details.aspx?id=55984)
