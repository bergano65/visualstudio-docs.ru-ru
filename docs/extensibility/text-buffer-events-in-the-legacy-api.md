---
title: "Текст события буфера в интерфейсе API прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>Текст события буфера в интерфейсе API прежних версий
Объект текстового буфера выдает несколько различных событий, которые позволяют реагировать на разных ситуациях.  
  
 При использовании API прежних версий, должны реализовывать следующие интерфейсы для получения уведомлений об изменениях в текстовом буфере. Предоставление интерфейсов в буфер текста с помощью `IConnectionPointContainer` изменяет интерфейс в текстовом буфере, чтобы получать уведомления об строки из буфера. Дополнительные сведения см. в разделе [как: регистрация для событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). В случае использования `IVsTextStreamEvents` или `IVsTextLinesEvents` интерфейсы, возвращаются изменения в любом одного или двух многомерные координатах, соответственно.  
  
## <a name="text-buffer-interfaces"></a>Интерфейсы текстового буфера  
 Ниже перечислены интерфейсы, реализуемые элементом объект текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (действия, сгруппированные в единое одной отмены или повтора).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Обеспечивает сохранность данных документа под управлением текстового буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; используется многими клиентами.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Обеспечивает чтение и запись возможности с помощью двухмерные координаты. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, поточно ориентированными, последовательный доступ к текста в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись возможности с помощью одномерный массив координат. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важным свойством является имя или моникера буфера. Случайные данные можно сохранить в буфере, с помощью этого интерфейса, создать GUID и использовать его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|  
  
## <a name="text-buffer-event-interfaces"></a>Интерфейсы событий текстового буфера  
 Ниже перечислены интерфейсы для уведомления о событии текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Уведомляет клиентов, когда новая служба языка связан с текстового буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Уведомляет клиентов при инициализации текстовый буфер, и при изменении данных в текстовом буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в одномерный массив координат.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в двухмерные координаты.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Уведомляет клиентов об изменениях в пользовательских данных.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Уведомляет клиентов последней фиксации жеста для запуска события и предоставляет диапазон изменения текста. `IVsPreliminaryTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, имеющих диспетчер отмены. `IVsPreliminaryTextChangeCommitEvents`Возникает перед другими событиями, например красивое, чтобы убедиться в том, что другие события, не изменяйте текст перед фиксацией изменений. VSPackage необходимо отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Уведомляет клиентов последней фиксации жеста для запуска события и предоставляет диапазон изменения текста. `IVsFinalTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, имеющих диспетчер отмены. `IVsFinalTextChangeCommitEvents`предназначен для использования только языковые службы или другие объекты, которые имеют полный контроль над редактирования. VSPackage необходимо отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к текстовый буфер с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Практическое руководство: регистрация для событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
