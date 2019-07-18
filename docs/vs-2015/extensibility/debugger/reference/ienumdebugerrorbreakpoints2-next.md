---
title: IEnumDebugErrorBreakpoints2::Next | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Next
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6cc6e27fc5e6ac5ad380a3168f55dd810fd9dcb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199670"
---
# <a name="ienumdebugerrorbreakpoints2next"></a>IEnumDebugErrorBreakpoints2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество извлекаемых элементов. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [in, out] Массив [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) элементов для заполнения.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически возвращенных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше, чем запрошенное количество элементов может быть возвращено; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
