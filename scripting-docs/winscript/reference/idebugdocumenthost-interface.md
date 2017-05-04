---
title: "Интерфейс IDebugDocumentHost | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost — интерфейс"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugDocumentHost
Предоставляет функциональность основного приложение\-, определенного как расцветка синтаксиса, в отладчике.  Метод `IDebugDocumentHelper::SetDebugDocumentHost` принимает этот интерфейс в качестве аргумента.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugDocumentHost` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Возвращает диапазон символов, которые были добавитьы с помощью `IDebugDocumentHelper::AddDeferredText`, в исходном документе основного приложения.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Возвращает атрибуты текста для блока текста документа.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Уведомляет основное приложение о том, что контекст создания нового документа, и позволяет основному приложению при необходимости, чтобы вернуть объект, элементы управления новый контекст.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Возвращает полный путь \(с именем файла\) исходного файла документа.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Возвращает имя документа, без информации пути.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Уведомляет основное приложение о том, что был сохранен файл источника документа, а его содержимое должно быть обновитьы.|