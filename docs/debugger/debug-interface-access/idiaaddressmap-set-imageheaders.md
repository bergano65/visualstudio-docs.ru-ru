---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap::set_imageHeaders - метод"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает заголовки образа, чтобы включить необходимые преобразования относительного виртуального адреса.  
  
## Синтаксис  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Параметры  
 cbData  
 \[in\] количество байтов данных заголовка.  Необходимо `n*sizeof(IMAGE_SECTION_HEADER)` где  `n` число заголовков разделов в исполняемом файле.  
  
 данные \[\]  
 \[in\] массив  `IMAGE_SECTION_HEADER` структуры, используемый для заголовков образа.  
  
 originalHeaders  
 \[in\] имеет значение `FALSE` если заголовки образа из нового образа,  `TRUE` если они автоматически устанавливают исходный образ до обновления.  Как правило, это будет присвоено `TRUE` только в сочетании с вызовами функции  [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 `IMAGE_SECTION_HEADER` структура объявляется в Winnt.h и представляет формат заголовка раздела образа исполняемого файла.  
  
 Относительного виртуального адреса зависит от вычисления `IMAGE_SECTION_HEADER` значения.  Обычно DIA извлекает данные из файла базы данных программы \(pdb\).  Если значения отсутствуют, DIA удалось вычислить относительные виртуальные адреса и [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) метод возвращает  `FALSE`.  Клиент должен затем вызвать метод [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) метод, чтобы включить относительного виртуального адреса вычисления после предоставления отсутствующие заголовки самих образа из образа.  
  
## См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)