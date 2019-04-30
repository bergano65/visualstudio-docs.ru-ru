---
title: IEnumDebugPortSuppliers2::GetCount | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::GetCount
helpviewer_keywords:
- IEnumDebugPortSuppliers2::GetCount
ms.assetid: 004f78dd-87d0-41a8-bcaa-f7fadbfeb8fc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abb44884769e000c719f720c186e00282f34ad12
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866666"
---
# <a name="ienumdebugportsuppliers2getcount"></a>IEnumDebugPortSuppliers2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает число элементов в перечислении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 [out] Возвращает число элементов в перечислении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является частью обычной интерфейса перечисления модели COM, который указывает, что только `Next`, `Clone`, `Skip`, и `Reset` методы должны быть реализованы.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
