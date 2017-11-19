---
title: "IDebugModule2::GetInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9d88f78d9f3942eb4744168c874a37db26dd144
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 [in, out] Объект [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуру, которая содержит описание модуля.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структура содержит имя модуля, который отображается в **модули** окна.  
  
## <a name="see-also"></a>См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)