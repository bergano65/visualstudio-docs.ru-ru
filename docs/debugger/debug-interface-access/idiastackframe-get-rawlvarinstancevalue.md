---
title: IDiaStackFrame::get_rawLVarInstanceValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69e6fc35d9ac5dcc57ffe136d88069003635fe8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Этот метод получает значение указанной локальной переменной в виде необработанных байт.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pInstance`  
 [in] `IDiaLVarInstance` Объект, представляющий экземпляр локальной переменной, чтобы получить значение.  
  
 `cbDataMax`  
 [in] Максимальное число байтов в буфере, на который указывает `pbData`. Это может быть до 8 байт (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Возвращает фактическое число байтов, сохраненных в буфере.  
  
 `pbData`  
 [out] Буфер для заполнены данными. Это не может быть `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)