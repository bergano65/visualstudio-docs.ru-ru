---
title: IDiaStackWalkHelper::readMemory | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af93d4d49167a6167d971140c3b668c95a34f799
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Считывает блок данных из исполняемого файла изображения в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 [in] Значение из [memorytypeenum-перечисление](../../debugger/debug-interface-access/memorytypeenum.md) перечисление, указывающее тип памяти для чтения.  
  
 VA  
 [in] Виртуальный адрес в образ, с которого начинается чтение.  
  
 `cbData`  
 [in] Размер буфера данных в байтах.  
  
 `pcbData`  
 [out] Возвращает число фактически считанных байтов. Если `pbData` — `NULL`, то это общее число байтов доступных данных.  
  
 `pbData`  
 [in, out] Буфер, заполнено чтения объем памяти.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)