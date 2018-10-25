---
title: IDebugArrayField::GetRank | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6921da02b2df62509dd820795581e3ce6dae92d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846243"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Возвращает ранг или число измерений массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwRank`  
 [out] Возвращает ранг.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Ранг массива соответствует число измерений. В C++ и C# многомерных массивов, массивы массивов на самом деле являются и таким образом можно считать одномерного массива (и `GetRank` метод всегда возвращает значение 1). В [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], с другой стороны, многомерные массивы обрабатываются по-разному и ранг такой массив отражает число измерений (и `GetRank` метод всегда возвращает число измерений).  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)