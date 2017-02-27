---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign - метод"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает выравнивание изображения.  
  
## Синтаксис  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Параметры  
 NewVal  
 \[in\] новое значение выравнивания образа для исполняемого файла.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Загруженные исполняемые файлы изображений \(\) выравниваются по указанным границ памяти.  Это выравнивание может зависеть от текущей системной архитектурой и которым следует компилировать и параметрами времени ссылки.  Выравнивание изображения всегда в диапазоне байта.  Допустимы следующие значения выравнивания образа. 1, 2, 4, 8, 16, 32 и 64 границе байта.  
  
 Текущее выравнивание изображения можно получить, вызвав [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) метод.  
  
> [!NOTE]
>  Образ уже загружен к моменту этот метод может быть вызван.  `put_imageAlign` метод обычно используется, когда был перемещен или был изменен способ выравнивания и создается новый.  
  
## См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)