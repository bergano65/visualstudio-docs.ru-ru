---
title: Событий текстового буфера в интерфейсе API для прежних версий | Документация Майкрософт
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
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 677824142f2e7e497888627041cfe7a82487d342
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735512"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Событий текстового буфера в интерфейсе API для прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект текстового буфера выдает несколько различных событий, которые позволяют реагировать на них различных ситуациях.  
  
 Если вы используете старый API, должны реализовывать следующие интерфейсы для получения уведомления об изменениях в текстовый буфер. Разработка интерфейсов для буфера текста с помощью `IConnectionPointContainer` изменяется интерфейс в текстовом буфере, чтобы получать уведомления об строки из буфера. Дополнительные сведения см. в разделе [как: регистрация для событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). В случае использования `IVsTextStreamEvents` или `IVsTextLinesEvents` интерфейсы, возвращаются изменения в любом одного или двух трехмерной координатах, соответственно.  
  
## <a name="text-buffer-interfaces"></a>Интерфейсы буфера текста  
 Ниже перечислены интерфейсы, реализованные объект текстового буфера.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Разрешает создание составных действий (то есть действия, которые группируются в единое единый отмены и повтора).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Включает сохранение данных документа, управляемых текстовым буфером.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Предоставляет базовые службы; Многие клиенты используют.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Предоставляет возможности, используя двухмерные координаты чтения и записи. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Обеспечивает быстрый, поточно ориентированный, последовательный доступ к текста в буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Обеспечивает чтение и запись с помощью одноразмерных координат. Наследует от `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Предоставляет доступ к общей коллекции свойств. Наиболее важным свойством является имя или моникер буфера. Случайные данные можно сохранить в буфере, с этим интерфейсом, создать GUID и использовать его в качестве ключа.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Поддерживает точки подключения для событий.|  
  
## <a name="text-buffer-event-interfaces"></a>Интерфейсы событий буфера текста  
 Ниже приведены интерфейсы для уведомления о событии текстового буфера.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Уведомляет клиентов, когда новая языковая служба связана с текстовым буфером.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Уведомляет клиентов, при инициализации текстового буфера, и при изменении данных в текстовом буфере.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в одномерный массив координат.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Уведомляет клиентов об изменениях в базовом текстовом буфере в двухмерные координаты.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Уведомляет клиентов об изменениях пользовательских данных.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие и предоставляет диапазон измененного текста. `IVsPreliminaryTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, которые имеют в диспетчере отмены. `IVsPreliminaryTextChangeCommitEvents` возникает до других событий, таких как красивое, чтобы убедиться, что другие события, не изменяйте текст перед фиксацией изменений. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Уведомляет клиентов о последнем жесте фиксации, инициирующем событие и предоставляет диапазон измененного текста. `IVsFinalTextChangeCommitEvents` Интерфейс не запускается в ответ для отмены или повтора команды. События возникают только для буферов, которые имеют в диспетчере отмены. `IVsFinalTextChangeCommitEvents` предназначен для использования только с помощью языковых служб или других объектов, имеющих полный контроль над изменением. VSPackage должен отслеживать либо `IVsPreliminaryTextChangeCommitEvents` интерфейс или `IVsFinalTextChangeCommitEvents` интерфейс, но не оба.|  
  
## <a name="see-also"></a>См. также  
 [Доступ к текстовый буфер с помощью API прежних версий](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Практическое руководство. Регистрация событий текстового буфера с помощью API прежних версий](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)

