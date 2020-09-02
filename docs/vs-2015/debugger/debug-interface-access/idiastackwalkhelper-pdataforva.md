---
title: Идиастакквалкхелпер::p Датафорва | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
 окне Указывает виртуальный адрес данных для получения.  
  
 `cbData`  
 окне Размер данных в байтах для получения.  
  
 `pcbData`  
 заполняет Возвращает фактический размер данных в байтах, которые были получены.  
  
 `pbData`  
 [вход, выход] Буфер, который заполняется запрошенными данными. Не может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если для указанного адреса не существует pData. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В разделе PDATA (раздел с именем ". pdata") компилируемого объекта содержатся сведения об обработке исключений для функций.  
  
 Вызывающий объект знает, сколько данных должно быть возвращено, поэтому вызывающему объекту не нужно запрашивать, сколько данных доступно. Таким образом, можно реализовать этот метод, чтобы он возвращал ошибку, если `pbData` параметр имеет значение `NULL` .  
  
## <a name="see-also"></a>См. также:  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
