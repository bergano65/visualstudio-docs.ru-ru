---
title: Предоставление скрытой поддержки текста в устаревшем языковом сервисе
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707930"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Как: Предоставить скрытую поддержку текста в устаревшей языковой службе
Можно создавать скрытые текстовые области в дополнение к набросным регионам. Скрытые текстовые области могут контролироваться клиентом или редактором и использоваться для полного сокрытия области текста. Редактор отображает скрытую область в виде горизонтальных линий. Примером этого является только представление **скрипта** в редакторе HTML.

## <a name="to-implement-a-hidden-text-region"></a>Реализация скрытого региона текста

1. `QueryService` Звоните <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>для .

     Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>на .

2. Вызов, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>проходя в указатель для данного буфера текста. Это определяет, существует ли уже скрытый сеанс текста для буфера.

3. Если он уже существует, то не нужно создавать один и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> указатель на существующий объект возвращается. Используйте этот указатель для перечисления и создания скрытых областей текста. В противном случае вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания скрытого сеанса текста для буфера.

     Возвращается указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> на объект.

    > [!NOTE]
    > При звонке `CreateHiddenTextSession`можно указать скрытый текстовый клиент (то есть, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Скрытый клиент текста уведомляет вас, когда скрытый текст или изложение расширяется или разрушается пользователем.

4. Звоните, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> чтобы добавить один или несколько новых областей `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>контура одновременно, указав следующую информацию в параметре ( )

    1. Укажите значение `hrtConcealed` в `iType` составе <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете скрытый регион, а не область контура.

        > [!NOTE]
        > Когда скрытые области скрыты, редактор автоматически отображает строки вокруг скрытых регионов, чтобы указать их присутствие.

    2. Укажите, контролируется ли регион клиентами `dwBehavior` или контролируется редактором в структурах. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Ваша интеллектуальная реализация может содержать сочетание наброски редакторов и клиентов и скрытых текстовых регионов.
