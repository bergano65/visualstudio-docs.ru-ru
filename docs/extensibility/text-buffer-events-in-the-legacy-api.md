---
title: "Событий текстового буфера в прежних версий API | Документы Microsoft"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7e7847cdca2065cadd6adaf0d4b3e6ea10444725
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Текст события буфера в API прежних версий
Объект текстового буфера создает несколько различных событий, которые позволяют реагировать на различных ситуациях.  
  
 При использовании предыдущих версий API, должен реализовать следующие интерфейсы для получения уведомлений об изменениях текстового буфера. Разработка интерфейсов для буфера текста с помощью `IConnectionPointContainer` изменяет интерфейс на текстовый буфер для получения уведомлений о строки из буфера. Дополнительные сведения см. в разделе [как: регистрация событий буфера текста с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). В случае использования `IVsTextStreamEvents` или `IVsTextLinesEvents` интерфейсы, возвращаются изменения в либо один или двусторонние многомерные координатах, соответственно.  
  
## <a name="text-buffer-interfaces"></a>Интерфейсы буфера текста  
 Ниже перечислены интерфейсы, реализованные объект текстового буфера.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Включает создание составных действий (действия, сгруппированные в единое один отмены и повтора).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение документа данных управляется буфер текста.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; используется многими клиентами.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет чтения и записи с помощью двумерные координаты. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Предоставляет быстрый, поточно ориентированный последовательный доступ к текста в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись возможности с помощью координат одномерный массив. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важные свойства — это имя, или моникер буфера. Случайные данные можно сохранить в буфере, с помощью этого интерфейса, создать GUID и использовать его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|  
  
## <a name="text-buffer-event-interfaces"></a>Интерфейсы событий буфера текста  
 Ниже перечислены интерфейсы для уведомления о событии буфера текста.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Сообщает клиенту при новой языковой службы, связанной с текстового буфера.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Сообщает клиенту, когда инициализируется буфер текста и при изменении данных в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Сообщает клиенту об изменениях к соответствующему буферу текста в одномерный массив координат.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Сообщает клиенту об изменениях к соответствующему буферу текста в двумерные координаты.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Сообщает клиенту об изменениях в данных пользователя.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Сообщает клиенту жеста последней фиксации для инициирования события, а также диапазон изменения текста. `IVsPreliminaryTextChangeCommitEvents` Интерфейс не срабатывает в ответ для отмены или повтора команды. События возникают только для буферов, имеющих диспетчер отмены. `IVsPreliminaryTextChangeCommitEvents`Возникает перед другими событиями, например автоматическое форматирование, чтобы убедитесь, что другие события, не изменяйте текст перед фиксацией изменений. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейса или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Сообщает клиенту жеста последней фиксации для инициирования события, а также диапазон изменения текста. `IVsFinalTextChangeCommitEvents` Интерфейс не срабатывает в ответ для отмены или повтора команды. События возникают только для буферов, имеющих диспетчер отмены. `IVsFinalTextChangeCommitEvents`предназначен для использования только с помощью служб языка или другие объекты, которые имеют полный контроль над редактирования. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейса или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к буфер текста с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Как: регистрация событий буфера текста с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)