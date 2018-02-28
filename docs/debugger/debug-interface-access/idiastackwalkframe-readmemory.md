---
title: "IDiaStackWalkFrame::readMemory | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4680b84ed3507316d628e8323b71e98cf2ccd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Считывает память из образа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 [in] Один из [memorytypeenum-перечисление](../../debugger/debug-interface-access/memorytypeenum.md) значений перечисления, которое указывает тип для доступа к памяти.  
  
 `va`  
 [in] Расположение виртуального адреса изображения должно начаться чтение.  
  
 `cbData`  
 [in] Размер буфера данных, в байтах.  
  
 `pcbData`  
 [out] Возвращает число байтов, возвращенных. Если `data` — `NULL`, затем `pcbData` содержит общее число байтов доступных данных.  
  
 `data`  
 [out] Буфер, который должен быть заполняется данными из указанного расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)