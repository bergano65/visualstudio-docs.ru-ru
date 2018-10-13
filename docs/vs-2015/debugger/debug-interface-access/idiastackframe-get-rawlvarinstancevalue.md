---
title: IDiaStackFrame::get_rawLVarInstanceValue | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 440a780ccd92a6f8f46f74c462e4adfc591c97ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175517"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Этот метод получает значение указанной локальной переменной в виде необработанных байт.  
  
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
 [in] `IDiaLVarInstance` Объект, представляющий экземпляр локальной переменной, чтобы получить значение.  
  
 `cbDataMax`  
 [in] Максимальное число байтов в буфере, на которые указывают `pbData`. Это может быть более 8 байт (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Возвращает фактическое число байтов, сохраненных в буфере.  
  
 `pbData`  
 [out] Буфер для заполниться данными. Не может иметь значение `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



