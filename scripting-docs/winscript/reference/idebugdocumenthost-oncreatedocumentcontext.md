---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
Уведомляет основное приложение о том, что контекст создания нового документа и позволяет основному приложению при необходимости, чтобы вернуть управление неизвестно для нового контекста.  
  
## Синтаксис  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### Параметры  
 `ppunkOuter`  
 \[out\] объект что элементы управления новый контекст.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Основное приложение не предоставляет управление объект.|  
  
## Заметки  
 Этот метод позволяет основному приложению, чтобы добавить новую функциональность в приложение\- aux, контексты документа.  Этот метод может возвращать нулевой **E\_NOTIMPL** или внешний объект, в этом случае вызывающий объект отвечает за создание контекста.  
  
## См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)