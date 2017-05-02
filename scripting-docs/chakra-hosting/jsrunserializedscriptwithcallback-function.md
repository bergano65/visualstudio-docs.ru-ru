---
title: "Функция JsRunSerializedScriptWithCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Функция JsRunSerializedScriptWithCallback
Запускает сериализованный скрипт. Предоставляет возможность отложенной загрузки источника скрипта, только если он нужен.  
  
## Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
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
 Результат выполнения скрипта \(если есть\). Этот параметр может быть нулевым.  
  
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