---
title: Практическое руководство. Поддержка скрытого текста в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3bec39ca044b0558dfeb9603137571a61c96548
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078854"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Практическое руководство. Поддержка скрытого текста в языковой службы прежних версий
Можно создавать области скрытого текста в дополнение к структурные области. Области скрытого текста может быть, управляемое клиентом или редактором и используются для полностью скрыть область текста. Редактор отображает скрытой области в виде горизонтальных линий. Примером этого является **только скрипт** представление в редакторе HTML.

## <a name="to-implement-a-hidden-text-region"></a>Для реализации области скрытого текста

1. Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.

     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера. Это определяет, существует ли уже сеанс скрытого текста для буфера.

3. Если он уже существует, то необходимо создать один и указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается объект. Используйте этот указатель для перечисления и создания области скрытого текста. В противном случае вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания сеанса скрытого текста для буфера.

     Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.

    > [!NOTE]
    >  При вызове `CreateHiddenTextSession`, можно указать клиент скрытого текста (т. е <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Клиент скрытого текста уведомления при скрытого текста или структурирование развернута или свернута пользователем.

4. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> для добавления одного или более новые структуры областей одновременно, указав следующие сведения в `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) параметра:

    1. Укажите значение `hrtConcealed` в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете скрытой области, а не область структуры.

        > [!NOTE]
        >  Если скрытые области скрыты, редактор автоматически отображает линии вокруг скрытых областей для обозначения их наличия.

    2. Укажите, является ли область, управляемая клиентом или редактором в `dwBehavior` членами <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Смарт-реализация структуры могут содержать как редактор и управляемая клиентом структуры и области скрытого текста.