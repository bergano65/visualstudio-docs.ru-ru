---
title: "Функция JsSerializeScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript - функция"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsSerializeScript
Сериализует проанализированный скрипт в буфер, который можно использовать повторно.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### Параметры  
 `script`  
 Скрипт для сериализации.  
  
 `buffer`  
 Буфер для размещения сериализованного скрипта.  Может быть равен null.  
  
 `bufferSize`  
 Размер буфера в байтах на входе; размер буфера в байтах, необходимый для хранения сериализованного скрипта, на выходе.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 `JsSerializeScript` анализирует скрипт и затем сохраняет проанализированную форму скрипта в независимом от среды выполнения формате.  Затем сериализованный скрипт можно десериализовать в любой среде выполнения без повторного анализа.  
  
 Требуется контекст активного скрипта.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)