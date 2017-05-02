---
title: "Метод IJsDebugDataTarget::ReadNullTerminatedString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::ReadNullTerminatedString
Считывает указанное число символов из целевого объекта.  
  
## Синтаксис  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Адрес, откуда производится чтение.  
  
 `characterSize`  
 \[in\] Размер каждого символа в строке  
  
 `maxCharacters`  
 \[in\] Максимальное количество считываемых символов. maxCharacters должно быть разумным.  Любой запрос на более чем 128 МБ памяти завершится ошибкой.  Если длина строки больше maxCharacters, результирующая строка будет усечена после maxCharacters.  
  
 `pString`  
 \[out\] Чтение BSTR чтения из целевого объекта.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает значение S\_FALSE, если усечено.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)