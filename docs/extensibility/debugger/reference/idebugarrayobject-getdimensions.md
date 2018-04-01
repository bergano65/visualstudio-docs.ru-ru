---
title: IDebugArrayObject::GetDimensions | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0e5297019470fe8f3fe314d542013850eab7f1e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Возвращает размерность массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwCount`  
 [in] Число измерений для извлечения.  
  
 `dwDimensions`  
 [in, out] Массив, который заполняется размеров каждого измерения. `dwCount`Указывает максимальный размер `dwDimensions` массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Многомерный массив может иметь различные размеры для каждого измерения. Например, при наличии трехмерный массив `myarray[3][2][6]`, этот метод возвращает 3, 2 и 6 в `dwDimensions` параметра в указанном порядке.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)