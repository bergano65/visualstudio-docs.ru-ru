---
title: IDebugModule2::GetInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8b35cb0d77f2e078cf8a66ae095a939e361fd46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007871"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Возвращает сведения об этом модуле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 [in] Сочетание флагов из [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) перечисление, указать, какие поля из `pInfo` , для заполнения.  
  
 `pInfo`  
 [in, out] Объект [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры, который заполняется описание модуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структура содержит имя модуля, который отображается в **модули** окна.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)