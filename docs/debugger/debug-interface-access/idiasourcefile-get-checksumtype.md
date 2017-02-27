---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType - метод"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает тип контрольной суммы.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает тип контрольной суммы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Тип контрольной суммы значение, которое может быть сопоставлено алгоритм контрольной суммы.  Например, стандартный формат файла PDB обычно может иметь одно из следующих значений:  
  
|Тип контрольной суммы|Метка CryptoAPI|Описание|  
|---------------------------|---------------------|--------------|  
|0|\<отсутствует\>|Без обращения к контрольной суммы.|  
|1|`CALG_MD5`|контрольная сумма, созданная с помощью алгоритма хэширования MD5.|  
|2|`CALG_SHA1`|контрольная сумма, созданная с помощью алгоритма хэширования SHA1.|  
  
 `CryptoAPI` метки из  `ALG_ID` перечисление.  Дополнительные сведения об алгоритмах хэширования, обратитесь к `CryptoAPI` раздел microsoft  [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Чтобы получить фактические байты контрольной суммы для файла источника, вызовите [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) метод.  
  
## См. также  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)