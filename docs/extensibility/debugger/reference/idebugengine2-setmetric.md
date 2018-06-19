---
title: IDebugEngine2::SetMetric | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12e323fe248bc022bcbbd8b9bdd0e628c27a97e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122851"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Этот метод задает значение реестра, известных как метрики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszMetric`  
 [in] Имя метрики.  
  
 `varValue`  
 [in] Указывает значение метрики.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Метрика — это значение реестра, используемый для изменения поведения модуля отладки или для объявления поддерживаемые функции. Этот метод может перенаправлять вызов соответствующей форме для [SDK вспомогательные методы для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функции `SetMetric`.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)