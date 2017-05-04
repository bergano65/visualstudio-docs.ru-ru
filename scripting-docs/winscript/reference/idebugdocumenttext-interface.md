---
title: "Интерфейс IDebugDocumentText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText — интерфейс"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugDocumentText
Предоставляет доступ к версии текста \- только документа отладки.  Этот интерфейс использует следующие соглашения:  
  
-   Номер линии и расположения символов и отсчитываются от нуля.  
  
-   Расположения символов, представляющих смещение знака; они не представляют смещение байтов или слов.  Для Win32, расположение смещения знаков Юникода.  
  
 В дополнение к методам, наследуемым от интерфейса `IDebugDocument`, интерфейс `IDebugDocumentText` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Возвращает атрибуты документа.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Возвращает количество линий и количество знаков в документе.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Возвращает позицию знака, соответствующее первому символу линии.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Возвращает номер линии и, при необходимости, смещение знака в линия, соответствующий данному расположению знаков.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Извлекает символы и атрибуты знака, связанные с диапазоном позиции символа.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Возвращает диапазон позиции символа, соответствующий контексту документа.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Создает объект контекста документа, соответствующий указанному диапазону позиции символа.|