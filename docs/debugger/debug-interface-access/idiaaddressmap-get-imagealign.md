---
title: "IDiaAddressMap::get_imageAlign | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap::get_imageAlign - метод"
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает текущее выравнивание изображения.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает значение выравнивания образа из исполняемого файла.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Образы выравниваются по конкретным границ памяти учитывается, как был загружен и для создания образа.  Выравнивание обычно на отметках 1, 2, 4, 8, 16, 32 или 64 байта диапазоне.  Выравнивание образа может быть установлен с вызовом [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) метод.  
  
## См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)