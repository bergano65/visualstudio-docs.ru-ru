---
title: "IDebugDocumentHelper::AddDBCSText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDBCSText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDBCSText"
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDBCSText
Добавляет строки двухбайтовой кодировки dbcs в конец этого документа.  
  
## Синтаксис  
  
```  
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### Параметры  
 `pszText`  
 \[in\] указатель на null\- завершенной строку, содержащую текст.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Метод не удалось добавить символы.|  
  
## Заметки  
 Этот метод создает уведомления `IDebugDocumentTextEvents`.  
  
> [!NOTE]
>  Если этот метод вызывается после того, как `IDebugDocumentHelper::AddDeferredText` было Позвонитьо, `E_FAIL` возвращается.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)