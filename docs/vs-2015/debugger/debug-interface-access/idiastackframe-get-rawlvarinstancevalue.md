---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573018"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Этот метод получает значение указанной локальной переменной в виде необработанных байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pInstance`  
 окне `IDiaLVarInstance` Объект, представляющий экземпляр локальной переменной, для которой нужно получить значение.  
  
 `cbDataMax`  
 окне Максимальное число байтов в буфере, на которое указывает `pbData` . Это может быть не более 8 байт ( `sizeof(ULONGLONG)` ).  
  
 `pcbData`  
 заполняет Возвращает фактическое число байтов, хранящихся в буфере.  
  
 `pbData`  
 заполняет Буфер для заполнения данными. Не может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
