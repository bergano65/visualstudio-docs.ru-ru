---
title: "IDebugReference2::SetValueAsString | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::SetValueAsString
helpviewer_keywords: IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41769e3c356294960cc5f4d58db77c0f190f13c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Задает значение ссылки из строки. Зарезервировано для будущего использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszValue`  
 [in] Значение в виде строки.  
  
 `dwRadix`  
 [in] Основание системы счисления, используемое в любой числовой сведения о форматировании.  
  
 `dwTimeout`  
 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)