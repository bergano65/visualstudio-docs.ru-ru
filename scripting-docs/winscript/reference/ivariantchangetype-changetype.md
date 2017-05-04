---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
Имеет другое значение и создается новый вариант с указанным типом.  
  
## Синтаксис  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### Параметры  
 `pvarDst`  
 \[in, out\] версия a, чтобы содержать значение, представленное `pvarSrc`, но с типом, указанным `vtNew`.  
  
 `pvarSrc`  
 \[in\] значение variant, подлежащий изменению в новый тип.  
  
 `lcid`  
 \[in\] контекст языкового стандарта для использования при преобразовании аргументы и строки.  
  
 `vtNew`  
 \[in\] указывает тип `pvarDst` для становления.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Аргументы `pvarDst` и `pvarSrc` могут быть равны, в которых учитывается исходное значение перезаписатьо.  Этот метод передает `pvarDst` функции `VariantClear`, и, следовательно, `pvarDst` должно быть инициализироватьо допустимое значение.  
  
## См. также  
 [Интерфейс IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)