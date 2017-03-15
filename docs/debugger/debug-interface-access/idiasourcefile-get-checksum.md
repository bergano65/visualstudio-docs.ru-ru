---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum - метод"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает байты контрольной суммы.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Параметры  
 `cbData`  
 \[in\] размер буфера данных в байтах.  
  
 `pcbData`  
 \[out\] возвращает число байтов контрольной суммы.  Этот параметр не может иметь значение `NULL`.  
  
 `data`  
 \[in, out\] буфер, который заполняется байт контрольной суммы.  Если этот параметр `NULL`после этого  `pcbData` возвращает необходимое число байтов.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Чтобы определить тип алгоритма контрольной суммы, который использовался для создания байты контрольной суммы, вызовите [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) метод.  
  
 Контрольная сумма обычно создается из исходного файла образа, поэтому отражены изменения в файле источника в изменениях в байтах контрольной суммы.  Если байты контрольной суммы не соответствуют контрольной суммы, созданной из загруженного файла образа, то файл должен быть повреждено или искажено учитывается.  
  
 Типичные контрольные суммы не более 32 байта, но не предполагать, что максимальный размер контрольной суммы.  Установка `data` параметр  `NULL` получить число байтов, необходимое для получения контрольная сумма.  Выберите буфер подходящего размера и этот метод следует вызывать несколько раз с новым буфером.  
  
## См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)