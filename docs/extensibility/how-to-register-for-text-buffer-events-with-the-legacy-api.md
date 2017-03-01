---
title: "Практическое руководство: регистрация для событий текстового буфера с помощью API прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Практическое руководство: регистрация для событий текстового буфера с помощью API прежних версий
Если вы обращаетесь в текстовом буфере с помощью API прежних версий, следует зарегистрировать для текстового буфера событий, как показано в следующей процедуре.  
  
### <a name="to-advise-text-buffer-events"></a>Чтобы уведомить событий текстового буфера  
  
1.  Из указателя на один из интерфейсов на <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, вызовите `QueryInterface` указатель <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  Вызов <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>метод и передайте идентификатор интерфейса событий, для которых вы хотите зарегистрировать.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     Например, если вы хотите зарегистрировать для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, передается в интерфейсе идентификатор IID_IVsTextLinesEvents.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     Текстовый буфер возвращает указатель на <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>интерфейс для объекта точки подключения.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  Используя этот указатель, позвоните <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>, передавая указатель на вашу реализацию интерфейса событий, для которого требуется зарегистрировать, например, `IVsTextLinesEvents` интерфейс.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     Среда возвращается cookie, который затем можно использовать для остановки прослушивание событий путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>метод.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>См. также  
 [Текст события буфера в интерфейсе API прежних версий](../extensibility/text-buffer-events-in-the-legacy-api.md)
