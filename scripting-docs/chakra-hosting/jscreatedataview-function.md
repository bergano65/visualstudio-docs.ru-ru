---
title: "Функция JsCreateDataView | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Функция JsCreateDataView
Создает объект `DataView` Javascript.  
  
## Синтаксис  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Параметры  
 `arrayBuffer`  
 Существующий объект `ArrayBuffer` для использования в качестве хранилища для объекта `DataView` результата.  
  
 `byteOffset`  
 Смещение в байтах от начала `arrayBuffer` для `DataView` результата до ссылки.  
  
 `byteLength`  
 Число байтов в буфере ArrayBuffer для DataView результата до ссылки.  
  
 `result`  
 Новый объект DataView.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Требуется контекст активного скрипта.  
  
 Этот API поддерживается только в режиме Edge.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)