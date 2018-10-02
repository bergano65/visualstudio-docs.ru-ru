---
title: IDebugProgramEngines2::EnumPossibleEngines | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 971c4d44cc5b12460b9f715a60537687665b0e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568220"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgramEngines2::EnumPossibleEngines](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines).  
  
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

