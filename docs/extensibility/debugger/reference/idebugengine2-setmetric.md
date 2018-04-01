---
title: IDebugEngine2::SetMetric | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 49208b4ef01d3f1a8cc22abe6d9a926089febed1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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