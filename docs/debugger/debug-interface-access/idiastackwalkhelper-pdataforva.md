---
title: IDiaStackWalkHelper::pdataForVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42ab689c5c94fcf0200775d9fdd59ac2a0f7202c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916981"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Возвращает блок данных PDATA, связанный с виртуальным адресом.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает виртуальный адрес для получения данных.  
  
 `cbData`  
 [in] Размер в байтах для получения данных.  
  
 `pcbData`  
 [out] Возвращает фактический размер данных в байтах, который был получен.  
  
 `pbData`  
 [in, out] Буфер, который заполняется запрошенные данные. Не может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` при наличии не PDATA по указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 PDATA (раздел, с именем «.pdata») содержит сведения об обработке исключений для функции единице компиляции.  
  
 Вызывающий объект знает, сколько данных возвращается, чтобы вызывающий объект не требуется обращаться к объему данных доступен. Таким образом, это допустимо для реализации этого метода будут возвращать ошибку, если `pbData` параметр `NULL`.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)