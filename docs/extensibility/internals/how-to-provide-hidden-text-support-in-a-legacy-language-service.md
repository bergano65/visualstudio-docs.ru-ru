---
title: Предоставление поддержки скрытого текста в языковой службе прежних версий
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707930"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Как обеспечить поддержку скрытого текста в языковой службе прежних версий
Помимо областей структуры, можно создавать скрытые текстовые области. Скрытые текстовые области могут быть управляемыми клиентом или редактором и используются для полного скрытия области текста. Редактор отображает скрытую область в виде горизонтальных линий. Примером этого является просмотр **только скриптов** в редакторе HTML.

## <a name="to-implement-a-hidden-text-region"></a>Реализация скрытой области текста

1. Вызовите метод `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> .

     Он возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> .

2. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> , передавая указатель на заданный текстовый буфер. Определяет, существует ли уже скрытый текстовый сеанс для буфера.

3. Если он уже существует, то не нужно создавать его, и возвращается указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект. Используйте этот указатель для перечисления и создания скрытых областей текста. В противном случае вызовите, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> чтобы создать скрытый текстовый сеанс для буфера.

     Возвращается указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект.

    > [!NOTE]
    > При вызове `CreateHiddenTextSession` можно указать скрытый текстовый клиент (т <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . е.). Скрытый текстовый клиент уведомляет вас, когда скрытый текст или структурирование развертывается или сворачивается пользователем.

4. Вызовите, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> чтобы добавить один или несколько новых областей структуры за раз, указав следующие сведения в `reHidReg` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> параметре ():

    1. Укажите значение в элементе `hrtConcealed` структуры, `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> чтобы указать, что создается скрытая область, а не область структуры.

        > [!NOTE]
        > Если скрытые области скрыты, редактор автоматически отображает строки вокруг скрытых областей, чтобы указать их присутствие.

    2. Укажите, является ли регион управляемым клиентом или управляемым редактором в `dwBehavior` членах <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Реализация интеллектуального структурирования может включать в себя сочетание структуры и скрытых текстовых областей, которые управляются редактором и клиентом.
