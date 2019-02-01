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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b1f58f31484084bff502d9ad6a019089ecfec8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992529"
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