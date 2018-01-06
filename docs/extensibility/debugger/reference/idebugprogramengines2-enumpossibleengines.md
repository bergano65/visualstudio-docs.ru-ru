---
title: "IDebugProgramEngines2::EnumPossibleEngines | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords: IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 81765959c0735080141ba8974387d592a461df25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Возвращает идентификаторы GUID для всех возможных отладчики (DE), можно отлаживать этой программы.  
  
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
 [in] Число DE GUID для возврата. Это также указывает максимальный размер `rgguidEngines` массива.  
  
 `rgguidEngines`  
 [in, out] Массив идентификаторов GUID DE заполнить.  
  
 `pceltEngines`  
 [out] Возвращает фактическое количество DE идентификаторы GUID, которые возвращаются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` или [C#] 0x8007007A, если буфер недостаточно велик.  
  
## <a name="remarks"></a>Примечания  
 Чтобы определить, сколько модулей существует, этот метод один раз с `celtBuffer` равным 0 и `rgguidEngines` параметра задать значение null. Возвращает `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A для C#) и `pceltEngines` параметр Возвращает размер буфера, необходимый.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)