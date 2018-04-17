---
title: Укажите структурирование поддержку в языковую службу | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Как: поддерживают расширенные структурирования в языковую службу прежних версий
Существует два варианта для расширения структуры поддержки для вашего языка только поддерживает **свернуть в определения** команды. Можно добавить управляемые редактор структурные области и добавить управляемая клиентом структурные области.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Добавив контролем редактор структурные области  
 Этот способ используется для создания области структуры, а затем разрешить редактора для обработки ли области развернут, свернут и так далее. Из двух вариантов для поддержки создания структуры этот параметр является наименее надежный. Для этого параметра можно создать новую область структуры через указанный фрагмент текста с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. После создания этой области, его поведение управляется редактора. Используйте следующую процедуру для реализации редактора управляемых структурные области.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Для реализации редактора управляемых структурную область  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указателя для данного текстового буфера. Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект в буфере.  
  
3.  Вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> для указателя на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> для добавления одного или более новые структуры областей одновременно.  
  
     Этот метод позволяет указать диапазон текста, структура ли удалены или сохранены существующих областей структуры и развернут или свернут по умолчанию структурную область.  
  
## <a name="adding-client-controlled-outline-regions"></a>Добавление областей структуры, управляемая клиентом  
 Используйте этот подход к структуре реализуйте управляемая клиентом (или смарт-), например, используемая [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] служб языка. Языковую службу, управляет собственный структурирование отслеживает содержимое текстового буфера удалить старый структурные области, когда они становится недействительным и при необходимости создавать новый структурные области.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Для реализации области Структура, управляемая клиентом  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указателя для данного текстового буфера. Определяет, существует ли уже сеанса скрытый текст в буфере.  
  
3.  Если текст сеанс уже существует, то необходимо создать один и указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается объект. Используйте этот указатель для перечисления и создают структурные области. В противном случае вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания сеанса скрытый текст в буфере. Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  
  
    > [!NOTE]
    >  При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, можно указать клиента скрытый текст (то есть <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> объекта). Этот клиент уведомляет вас скрытый текст или структурную область развернут или свернут пользователем.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> структуры) параметра: задайте значение <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете структурную область, а не скрытые области. Укажите, является ли область управляемая клиентом или редактор контролируемых в `dwBehavior` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Смарт-структурирования реализации может содержать сочетание редактора и управляет клиент структурные области. Укажите текст заголовка, отображаемый, когда ваш структурную область свернута, такие как «...», в `pszBanner` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Текст баннера редактора по умолчанию для скрытой области — «...».