---
title: 'Практическое: поддержка скрытого текста в языковой службе прежних версий | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b689bdfff45f12bc85f79b3cba8581e728c89728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561740"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>Практическое: поддержка скрытого текста в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: предоставить скрытые поддержка текста в языковой службе прежних версий](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service).  
  
Можно создавать области скрытого текста в дополнение к структурные области. Области скрытого текста может быть, управляемое клиентом или редактором и используются для полностью скрыть область текста. Редактор отображает скрытой области в виде горизонтальных линий. Примером этого является представлением только скрипт в редакторе HTML.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-implement-a-hidden-text-region"></a>Для реализации области скрытого текста  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера. Это определяет, существует ли уже сеанс скрытого текста для буфера.  
  
3.  Если он уже существует, то необходимо создать один и указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается объект. Используйте этот указатель для перечисления и создания области скрытого текста. В противном случае вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания сеанса скрытого текста для буфера.  
  
     Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  
  
    > [!NOTE]
    >  При вызове `CreateHiddenTextSession`, можно указать клиент скрытого текста (т. е <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). Клиент скрытого текста уведомления при скрытого текста или структурирование развернута или свернута пользователем.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> для добавления одного или более новые структуры областей одновременно, указав следующие сведения в `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) параметра:  
  
    1.  Укажите значение `hrtConcealed` в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете скрытой области, а не область структуры.  
  
        > [!NOTE]
        >  Если скрытые области скрыты, редактор автоматически отображает линии вокруг скрытых областей для обозначения их наличия.  
  
    2.  Укажите, является ли область, управляемая клиентом или редактором в `dwBehavior` членами <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Смарт-реализация структуры могут содержать как редактор и управляемая клиентом структуры и области скрытого текста.

