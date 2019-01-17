---
title: IDiaStackWalkFrame::readMemory | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00171e470bd5dfd2a64bf7faabb0e338eceed7b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874669"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Читает содержимое памяти на основе образа.  
  
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
 [in] Один из [перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) значений перечисления, указывающее тип доступа к памяти.  
  
 `va`  
 [in] Виртуальный адрес расположения в образе должно начаться чтение.  
  
 `cbData`  
 [in] Размер буфера данных, в байтах.  
  
 `pcbData`  
 [out] Возвращает количество байтов, возвращаемых. Если `data` — `NULL`, затем `pcbData` содержит общее число байтов доступных данных.  
  
 `data`  
 [out] Буфер, который должен заполниться данными из указанного расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)