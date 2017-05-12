---
title: "Функция JsAddRef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef - функция"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция JsAddRef
Добавляет ссылку на объект, в котором был собран мусор.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### Параметры  
 `ref`  
 Объект для добавления ссылки.  
  
 `count`  
 Новое количество ссылок объекта \(может передать значение null\).  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
 Этот метод нужно вызывать только в дескрипторах `JsRef`, которые не планируется хранить где\-нибудь в стеке.  Вызов `JsAddRef` гарантирует, что объект, на который ссылается `JsRef`, не будет освобожден до вызова метода `JsRelease`.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)