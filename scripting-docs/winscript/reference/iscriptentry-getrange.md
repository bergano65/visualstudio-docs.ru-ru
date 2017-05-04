---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
Возвращает начальное положение и размер записи.  
  
## Синтаксис  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### Параметры  
 `pichMin`  
 \[out\] `IScriptEntry` для объектов, которые определяют блок скрипта, return 0.  
  
 Для объектов `IScriptEntry`, определяющие объект функции, функции возвращают начальную позицию в текущем блоке скрипта.  
  
 Для объектов, `IScriptScriptlet` возвращают 0.  
  
 `pcch`  
 \[out\] `IScriptEntry` для объектов, которые определяют блок скрипта, передачи длина текста.  
  
 Для объектов `IScriptEntry`, определяющие объект функции извлечения длина определения функции.  
  
 Для объектов `IScriptScriptlet`, передачи длина записи.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)