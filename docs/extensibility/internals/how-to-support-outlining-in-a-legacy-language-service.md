---
title: 'Как: Поддержка С изложением в Устаревшей языковой службе (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707918"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Как: Поддержка с изложением в устаревшей языковой службе
Изложение используется для расширения или краха различных областей текста. Способ использования излагаются могут быть определены по-разному по разным языкам. Дополнительные сведения см. в разделе [Структура](../../ide/outlining.md).

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации, смотрите [Прогулка: Описание](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

 Ниже показано, как поддерживать эту команду для вашей языковой службы.

## <a name="to-support-outlining"></a>Для поддержки изложения

1. Реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> на объекте языкового обслуживания.

2. Призыв <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> к текущему объекту с изложением сеанса добавить новые области контуров.

## <a name="robust-programming"></a>Отказоустойчивость
 Когда пользователь выбирает **«Свернуть к определениям»** в меню **«Изложение»,** IDE вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> вашу языковую службу.

 Когда этот метод вызывается, IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> проходит в указатель (указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> текстовый буфер) и (указатель на текущий сеанс изложения).

 Можно вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> метод для нескольких областей контура, указав эти области в параметре. `rgOutlnReg` Параметр `rgOutlnReg` представляет <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> собой структуру. Этот процесс позволяет указать различные характеристики скрытого региона, например, расширяется или разрушается ли конкретный регион.

> [!NOTE]
> Будьте осторожны, скрывая новые символы. Скрытый текст должен распространяться от начала первой строки до последнего символа последней строки в разделе, оставляя видимым окончательный символ новой строки.

## <a name="see-also"></a>См. также
- [Как: Предоставить скрытую поддержку текста в устаревшей языковой службе](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Как: Обеспечить расширенную поддержку с изложением в устаревшей языковой службе](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
