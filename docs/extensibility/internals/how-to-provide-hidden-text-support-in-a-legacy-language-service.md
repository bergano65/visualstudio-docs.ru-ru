---
title: "Как: обеспечивают поддержку скрытый текст в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7aab5978d2fc5f7bee82b097ed61a9603d7e198
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Как: обеспечивают поддержку скрытый текст в языковую службу прежних версий
Можно создавать области скрытый текст в дополнение к структурные области. Скрытый текст области могут быть как управляемая клиентом или редактор управляемых и используются, чтобы полностью скрыть область текста. Редактор отображает скрытые области в виде горизонтальных линий. Примером этого является представлением только скрипт в редакторе HTML.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-implement-a-hidden-text-region"></a>Для реализации область скрытого текста  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указателя для данного текстового буфера. Определяет, существует ли уже сеанса скрытый текст в буфере.  
  
3.  Если он уже существует, то необходимо создать один и указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается объект. Используйте этот указатель для перечисления и создания областей скрытый текст. В противном случае вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания сеанса скрытый текст в буфере.  
  
     Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  
  
    > [!NOTE]
    >  При вызове `CreateHiddenTextSession`, можно указать клиента скрытый текст (то есть, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Скрытый текст клиент уведомляет о скрытого текста или структурирование развернут или свернут пользователем.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> для добавления одного или более новые структуры областей одновременно, указав следующие сведения в `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) параметра:  
  
    1.  Укажите значение `hrtConcealed` в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете скрытые области, а не структурную область.  
  
        > [!NOTE]
        >  Если скрыты скрытые области, редактор автоматически отображает линии вокруг скрытые области, чтобы указать их наличие.  
  
    2.  Укажите, является ли область управляемая клиентом или редактор контролируемых в `dwBehavior` члены <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Смарт-структурирования реализации могут содержать как редактор и управляет клиента структуры и областей скрытый текст.