---
title: "Обеспечивают структурирование поддержки в языковую службу | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: fc502e4430a49284cffe14386249999d82085f1c
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Практическое руководство: обеспечивают расширенную поддержку создания структуры в языковую службу для прежних версий
Существует два варианта расширения структуры поддержки для вашего языка только поддерживает **свернуть в определения** команды. Можно добавить управляемые редактор структурные области и добавить управляемая клиентом структурные области.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Добавление областей структуры контролируемые редактора  
 Этот способ используется для создания области структуры, а затем разрешить редактор для обработки ли область развернут, свернут и т.д. Из двух вариантов для структурирования поддержки этот параметр является наименее надежный. Для этого параметра можно создать новую область структуры через указанный фрагмент текста с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> После создания этой области его поведение контролируется с помощью редактора. Используйте следующую процедуру для реализации редактора управлением структурные области.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Для реализации редактора управлением структурную область  
  
1.  Вызов `QueryService` для<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager></xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>объект буфера.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
3.  Вызов <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> </xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>  
  
4.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>для добавления одного или более новые структуры областей одновременно.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>  
  
     Этот метод позволяет указать диапазон текста структуры ли удалить или сохранить существующих областей структуры и ли развернут или свернут по умолчанию области структуры.  
  
## <a name="adding-client-controlled-outline-regions"></a>Добавление областей структуры, управляемая клиентом  
 Используйте этот подход к структуре реализуйте управляемая клиентом (или смарт-), используемые как [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] языковые службы. Служба языка, которая управляет собственный структурирование отслеживает текстовое содержимое буфера чтобы уничтожить старые структурные области, когда они становится недействительным и при необходимости создайте новые области структуры.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Для реализации регион структура, управляемая клиентом  
  
1.  Вызов `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Это возвращает указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> Определяет, существует ли уже сеанс скрытого текста в буфере.  
  
3.  Если текст сеанс уже существует, то необходимо создать один и указатель на существующие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>возвращается объект.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Используйте этот указатель для перечисления и создавать структурные области. В противном случае — вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>для создания сеанса скрытого текста в буфере.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>объект возвращается.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>  
  
    > [!NOTE]
    >  При вызове метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, можно указать клиента скрытый текст (то есть, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>объект).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> Этот клиент уведомляет о том, когда скрытого текста или развернут или свернут пользователем области структуры.  
  
4.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>структуры) параметра: укажите значение <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>структуры, чтобы указать, что вы создаете структурную область, а не в скрытой области.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> </xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> Укажите, является ли область управляемая клиентом или редактор контролируемых в `dwBehavior` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>структуры.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Смарт-реализации структуры может содержать сочетание структурные области редактора и управляемая клиентом. Укажите текст баннера, который отображается свернутым вашего региона структуры, такие как «...», в `pszBanner` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>структуры.</xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Текст баннера по умолчанию редактора для скрытой области — «...».
