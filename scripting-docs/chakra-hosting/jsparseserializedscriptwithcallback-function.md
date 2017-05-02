---
title: "Функция JsParseSerializedScriptWithCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a93ecfb-4b82-4a85-b24c-6816db2332ea
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция JsParseSerializedScriptWithCallback
Анализирует сериализованный скрипт и возвращает функцию, представляющую этот скрипт. Предоставляет возможность отложенной загрузки источника скрипта, только если он нужен.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_ JsValueRef * result  
);  
  
```  
  
#### Параметры  
 `scriptLoadCallback`  
 Обратный вызов выполняется, когда нужно загрузить исходный код скрипта.  
  
 `scriptUnloadCallback`  
 Обратный вызов выполняется, когда сериализованный скрипт и исходный код больше не нужны.  
  
 `buffer`  
 Сериализованный скрипт.  
  
 `sourceContext`  
 Файл cookie, указывающий на скрипт, который может использоваться контекстами отлаживаемых скриптов. Этот контекст будет передан в scriptLoadCallback и scriptUnloadCallback.  
  
 `sourceUrl`  
 Исходное местоположение скрипта.  
  
 `result`  
 Функция, представляющая код скрипта.  
  
## Возвращаемое значение  
 Код `JsNoError`, если операция завершилась успешно, если нет, то код сбоя.  
  
## Заметки  
  
> [!NOTE]
>  Этот API пока не доступен для приложений Магазина.  
  
 Требуется контекст активного скрипта.  
  
 Среда выполнения будет удерживать буфер, пока все экземпляры любых функций, созданных из буфера, не будут удалены сборкой мусора.  Затем она вызывает scriptUnloadCallback для информирования вызывающего объекта, что освободить безопасно.  
  
## Требования  
 **Заголовок:** jsrt.h  
  
## См. также  
 [Справочник \(среда выполнения JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)