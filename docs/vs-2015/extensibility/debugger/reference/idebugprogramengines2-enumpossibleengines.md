---
title: IDebugProgramEngines2::EnumPossibleEngines | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a417fd4f0d90ffebd291179dee28a0e81f92cce9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978832"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает идентификаторы GUID для всех возможных отладчики (DE), которые можно отлаживать этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
