---
title: События текстового буфера в устаревшем API | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186406"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>События текстового буфера в интерфейсе API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект текстового буфера создает несколько различных событий, которые позволяют реагировать на различные ситуации.  
  
 При использовании устаревшего API следует реализовать следующие интерфейсы, чтобы получить уведомления об изменениях в текстовом буфере. Предоставьте интерфейсы текстовому буферу, используя `IConnectionPointContainer` интерфейс в текстовом буфере для получения уведомлений об изменениях строк из буфера. Дополнительные сведения см. в разделе [инструкции. Регистрация для событий текстового буфера с помощью устаревшего API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). В случае `IVsTextStreamEvents` `IVsTextLinesEvents` интерфейсов или изменения возвращаются в виде одной или двух двумерных координат соответственно.  
  
## <a name="text-buffer-interfaces"></a>Интерфейсы текстовых буферов  
 Ниже приведены интерфейсы, реализуемые объектом текстового буфера.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (то есть действия, сгруппированные в одну единицу отмены или возврата).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение данных документа, управляемого с помощью текстового буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы. используется многими клиентами.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет возможности чтения и записи с помощью двумерных координат. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, ориентированный на поток последовательный доступ к тексту в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Предоставляет возможности чтения и записи, используя одномерные координаты. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к универсальной коллекции свойств. Наиболее важным свойством является имя или моникер буфера. Вы можете хранить собственные случайные данные в буфере с помощью этого интерфейса, создавая GUID и используя его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки соединения для событий.|  
  
## <a name="text-buffer-event-interfaces"></a>Интерфейсы событий текстового буфера  
 Ниже приведены интерфейсы для уведомления о событиях текстовых буферов.  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Уведомляет клиентов о создании связи между новой языковой службой и текстовым буфером.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Уведомляет клиентов при инициализации текстового буфера и при внесении изменений в данные в текстовом буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в одномерных координатах.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в двумерных координатах.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Уведомляет клиентов об изменениях пользовательских данных.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие, и предоставляет диапазон измененного текста. `IVsPreliminaryTextChangeCommitEvents`Интерфейс не запускается в ответ на команды отмены или повтора. События срабатывают только для буферов с диспетчером отмены. `IVsPreliminaryTextChangeCommitEvents` вызывается до других событий, например для отображения, чтобы убедиться, что другие события не изменяют текст до фиксации изменений. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс `IVsFinalTextChangeCommitEvents` , либо интерфейс, но не оба.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие, и предоставляет диапазон измененного текста. `IVsFinalTextChangeCommitEvents`Интерфейс не запускается в ответ на команды отмены или повтора. События срабатывают только для буферов с диспетчером отмены. `IVsFinalTextChangeCommitEvents` предназначен для использования только службами языка или другими объектами, которые имеют полный контроль над редактированием. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс `IVsFinalTextChangeCommitEvents` , либо интерфейс, но не оба.|  
  
## <a name="see-also"></a>См. также:  
 [Доступ к текстовому буферу с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Практическое руководство. Регистрация событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
