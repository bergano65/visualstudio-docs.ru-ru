---
title: Предоставление поддержки структурирования в языковой службе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 450ef1430e86467d116cc635a27600756bc36075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905286"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Руководство. Предоставление расширенной поддержки структурирования в языковой службе прежних версий
Существует два варианта расширения поддержки структурирования для вашего языка, помимо поддержки команды **Свернуть в определения** . Можно добавить области структуры, управляемые редактором, и добавить области структуры, управляемые клиентом.

## <a name="adding-editor-controlled-outline-regions"></a>Добавление областей структуры, управляемых редактором
 Используйте этот подход для создания области структуры, а затем разрешите редактору, что область разворачивается, сворачивается и т. д. Из двух вариантов предоставления поддержки структурирования этот параметр является наименее надежным. Для этого параметра вы создаете новую область структуры на основе указанного фрагмента текста с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . После создания этого региона его поведение управляется редактором. Следующая процедура используется для реализации областей структуры, управляемых редактором.

### <a name="to-implement-an-editor-controlled-outline-region"></a>Реализация области структуры, управляемой редактором

1. Вызов `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     Он возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , передавая указатель на заданный текстовый буфер. Он возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект для буфера.

3. Вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> On <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> для указателя на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> .

4. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> , чтобы добавить один или несколько новых областей структуры за раз.

     Этот метод позволяет указать диапазон текста для структурирования, необходимость удаления или сохранения существующих областей структуры, а также по умолчанию разворачивать или сворачивать область структуры.

## <a name="add-client-controlled-outline-regions"></a>Добавление областей структуры, управляемых клиентом
 Используйте этот подход, чтобы реализовать управляемую клиентом (или интеллектуальную) структуру, подобную используемой [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] службами языка и. Языковая служба, управляющая собственной структурой, отслеживает содержимое текстового буфера для уничтожения старых областей структуры, когда они становятся недействительными, и для создания новых областей структуры по мере необходимости.

### <a name="to-implement-a-client-controlled-outline-region"></a>Реализация области структуры, управляемой клиентом

1. Вызовите метод `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Он возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , передавая указатель на заданный текстовый буфер. Определяет, существует ли уже скрытый текстовый сеанс для буфера.

3. Если текстовый сеанс уже существует, то создавать его не нужно, и возвращается указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект. Используйте этот указатель для перечисления и создания областей структуры. В противном случае вызовите, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> чтобы создать скрытый текстовый сеанс для буфера. Возвращается указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект.

    > [!NOTE]
    > При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> можно указать скрытый текстовый клиент (т <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . е. объект). Этот клиент уведомляет вас о том, что скрытый текст или область структуры развернуты или свернуты пользователем.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>Структура вызова) параметр: Укажите значение в элементе <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что создается область структуры, а не скрытая область. Укажите, является ли регион управляемым клиентом или управляемым редактором в элементе `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Реализация интеллектуального структурирования может содержать различные регионы структуры, управляемые редактором и клиентами. Укажите текст баннера, который будет отображаться при свертывании области структуры, например "...", в элементе `pszBanner` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Текст баннера редактора по умолчанию для скрытой области — "...".
