---
title: 'Идебугаррайфиелд:: Rank | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198734"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает ранг или количество измерений массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 заполняет Возвращает ранг.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Ранг массива соответствует числу измерений. В C++ и C# многомерные массивы являются массивами массивов и поэтому могут рассматриваться только как одномерные массивы (и `GetRank` метод всегда возвращает 1). В с [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] другой стороны многомерные массивы обрабатываются по-разному, а ранг такого массива отражает количество измерений (и `GetRank` метод всегда возвращает количество измерений).  
  
## <a name="see-also"></a>См. также:  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
