---
title: "Метод IJsDebugDataTarget::ReadBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::ReadBSTR
Читает BSTR из целевого объекта отладки.  
  
## Синтаксис  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### Параметры  
 `address`  
 \[in\] Адрес, откуда производится чтение.  
  
 `pString`  
 \[out\] Чтение BSTR чтения из целевого объекта отладки.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS, если адрес недопустим.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)