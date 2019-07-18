---
title: IDiaStackWalkHelper::pdataForVA | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150091"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает блок данных PDATA, связанный с виртуальным адресом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
