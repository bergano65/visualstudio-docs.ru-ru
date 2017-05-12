---
title: "IDebugDocumentHelper::AddUnicodeText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddUnicodeText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddUnicodeText"
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddUnicodeText
Добавляет строку Юникода к концу данного документа.  
  
## Синтаксис  
  
```  
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
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
>  Если этот метод вызывается после того, как `AddDeferredText` было Позвонитьо, `E_FAIL` возвращается.  
  
## См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)