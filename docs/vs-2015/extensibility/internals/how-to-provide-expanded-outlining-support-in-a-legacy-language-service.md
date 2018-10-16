---
title: 'Практическое: Расширенная поддержка структурирования в языковой службе прежних версий | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6371339da12d88832e84d5086ed2d8a83226a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239544"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Практическое: Расширенная поддержка структурирования в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Существует два варианта для расширения структуры поддержки для вашего языка, чем поддержка **свернуть в определения** команды. Вы можете добавить редактором структурные области, а также добавить управляемая клиентом структурные области.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Добавление редактором структурные области  
 Этот способ используется для создания область структуры, а затем разрешить редактор для обработки ли область развернута, свернуты и так далее. Из двух вариантов для предоставления поддержка структурирования этот параметр является наименее надежный. Для этого параметра, создании новой области структуры на заданный диапазон текста с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. После создания этот регион, его поведение контролируется с помощью редактора. Используйте следующую процедуру для реализации редактором структурные области.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Для реализации редактором структурную область  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера. Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект для буфера.  
  
3.  Вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> для указателя на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> для добавления одного или более новые структуры регионах одновременно.  
  
     Этот метод позволяет указать диапазон текста, структуры, является ли удаление или сохранение существующих областей структуры и ли область структуры развернута или свернута по умолчанию.  
  
## <a name="adding-client-controlled-outline-regions"></a>Добавление областей структуры, управляемая клиентом  
 Используйте этот подход к структуре реализуйте управляемая клиентом (или смарт-), например, используемые [!INCLUDE[csprcs](../../includes/csprcs-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] языковых служб. Языковой службы, которая управляет свой собственный структурирование отслеживает содержимое текстового буфера удалить старый структурные области в том случае, когда они становится недействительным и при необходимости, создавать новые структурные области.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Для реализации область структуры, управляемая клиентом  
  
1.  Вызовите `QueryService` для <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, передавая указатель для данного текстового буфера. Это определяет, существует ли уже сеанс скрытого текста для буфера.  
  
3.  Если текст сеанс уже существует, то необходимо создать один и указатель на существующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> возвращается объект. Используйте этот указатель для перечисления и создания структурные области. В противном случае вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> для создания сеанса скрытого текста для буфера. Указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> объект возвращается.  
  
    > [!NOTE]
    >  При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, можно указать клиент скрытого текста (т. е <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> объекта). Этот клиент уведомляет вас, когда скрытый текст или область структуры развернута или свернута пользователем.  
  
4.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> структуры) параметра: укажите значение <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> в `iType` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры, чтобы указать, что вы создаете область структуры, а не скрытую область. Укажите, является ли область, управляемая клиентом или редактором в `dwBehavior` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Смарт-реализация структуры может содержать смесь структурные области редактора и управляемая клиентом. Укажите текст заголовка, отображаемый, когда ваш структурная область свернута, такие как «...» в `pszBanner` членом <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> структуры. Текст баннера по умолчанию редактора для скрытой области — «...».

