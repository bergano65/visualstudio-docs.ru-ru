---
title: "IDebugArrayObject2::HasBaseIndices | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf293eacb64fdee5790ff9b87d2e3afcfccc8f2d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
Определяет, имеет ли массив базовые индексы (нижнюю границу) определен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```csharp  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfHasBaseIndices`  
 [out] Значение TRUE, чтобы указать, что массив имеет базовый индексов (нижнюю границу); в противном случае — значение FALSE.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.