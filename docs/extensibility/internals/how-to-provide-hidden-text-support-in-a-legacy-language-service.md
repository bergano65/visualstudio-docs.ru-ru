---
title: 'Как: обеспечивают поддержку скрытый текст в языковую службу прежних версий | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54e508c6bcbb9cb79459e0b61a97f51350c00708
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132646"
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