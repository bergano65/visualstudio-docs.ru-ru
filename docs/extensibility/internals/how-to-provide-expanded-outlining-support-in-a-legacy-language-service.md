---
title: Предоставление поддержки в языковой службе (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707967"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Как: Обеспечить расширенную поддержку с изложением в устаревшей языковой службе
Существует два варианта расширения поддержки вашего языка, помимо поддержки команды **«Обюгирование» команде «Определения».** Можно добавить регионы контура, контролируемые редактором, и добавить регионы контура, контролируемые клиентами.

## <a name="adding-editor-controlled-outline-regions"></a>Добавление регионов, контролируемых редактором, набросков
 Используйте этот подход, чтобы создать область контуров, а затем позвольте редактору справиться с тем, расширяется ли область, разрушается и так далее. Из двух вариантов предоставления поддержки этот вариант является наименее надежным. Для этой опции создается новая область контура <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>на указанном диапазоне текста с использованием. После создания этого региона его поведение контролируется редактором. Используйте следующую процедуру для реализации регионов, контролируемых редактором, набросков.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Реализация региона контура, контролируемого редактором

1. Звоните `QueryService` для<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>на .

2. Вызов, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>проходя в указатель для данного буфера текста. Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объекту для буфера.

3. <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> Позвоните <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> для указателя <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>на .

4. Призыв <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> добавлять один или несколько новых регионов контура одновременно.

     Этот метод позволяет определить диапазон текста для набросков, удалены или сохранены существующие области контура, а также расширение или сворачивание области контура по умолчанию.

## <a name="add-client-controlled-outline-regions"></a>Добавление регионов контура, контролируемого клиентами
 Используйте этот подход для реализации контролируемых клиентом (или умных) с изложением, как тот, который используется [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] языковых служб. Языковая служба, управляющая собственным изложением, отслеживает содержимое буфера текста, чтобы уничтожить старые области контуров, когда они становятся недействительными, и создавать новые области контуров по мере необходимости.

### <a name="to-implement-a-client-controlled-outline-region"></a>Реализация региона, контролируемого клиентом,

1. `QueryService` Звоните <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>для . Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>на .

2. Вызов, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>проходя в указатель для данного буфера текста. Это определяет, существует ли уже скрытый сеанс текста для буфера.

3. Если сеанс текста уже существует, то не нужно его создавать, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается указатель на существующий объект. Используйте этот указатель для перечисления и создания областей контура. В противном случае вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания скрытого сеанса текста для буфера. Возвращается указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> на объект.

    > [!NOTE]
    > При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>можно указать скрытый текстовый <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> клиент (т.е. объект). Этот клиент уведомляет вас, когда скрытый текст или область контура расширяется или разрушается пользователем.

4. Структура <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> вызова) параметр: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> Укажите `iType` значение <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> в элементе структуры, чтобы указать, что вы создаете область контура, а не скрытый регион. Укажите, контролируется ли регион клиентом `dwBehavior` или контролируется редактором в составе <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Ваша интеллектуальная реализация может содержать сочетание регионов, контролируемых редакторами и клиентами. Укажите текст баннера, отображаемый при обрушении области `pszBanner` контура, <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> например "...", в члене структуры. Текст баннера редактора по умолчанию для скрытого региона — «...».
