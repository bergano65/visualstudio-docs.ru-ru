---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
Метод `Init` инициализирует вспомогательный объект документа отладку с именем и начальными атрибутами.  
  
## Синтаксис  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### Параметры  
 `pda`  
 \[in\] отладке приложения, связанное с этим документом.  
  
 `pszShortName`  
 \[in\] значение null\- завершенных строка, содержащая короткое имя документа.  
  
 `pszLongName`  
 \[in\] значение null\- завершенных строка, содержащая длинное имя документа.  
  
 `docAttr`  
 \[in\] определяет атрибуты текстового документа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод инициализирует вспомогательный объект документа отладку с именем и начальными атрибутами.  
  
 Этот документ не отображается в дереве до тех пор, пока не `IDebugDocumentHelper::Attach` Позвонитьо.  
  
## См. также  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Константы TEXT\_DOC\_ATTR](../../winscript/reference/text-doc-attr-constants.md)