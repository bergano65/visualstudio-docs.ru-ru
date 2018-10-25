---
title: IDebugProgramEngines2::EnumPossibleEngines | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f5977e7dbac34e247838efe1e8d0036e60f0416
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887676"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Возвращает идентификаторы GUID для всех возможных отладчики (DE), которые можно отлаживать этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```csharp  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celtBuffer`  
 [in] Число GUID DE для возврата. Это также указывает максимальный размер `rgguidEngines` массива.  
  
 `rgguidEngines`  
 [in, out] Массив идентификаторов GUID DE для заполнения.  
  
 `pceltEngines`  
 [out] Возвращает фактическое количество GUID DE, которые возвращаются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` или [C#] 0x8007007A, если буфер недостаточно велик.  
  
## <a name="remarks"></a>Примечания  
 Чтобы определить, сколько антивирусных ядер, этот метод вызывается один раз со `celtBuffer` параметр значение 0 и `rgguidEngines` параметру присвоить значение null. Эта команда возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A для C#) и `pceltEngines` параметр Возвращает нужного размера буфера.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)