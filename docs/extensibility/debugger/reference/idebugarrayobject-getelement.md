---
title: "IDebugArrayObject::GetElement | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetElement
helpviewer_keywords: IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 451c758ef067bfd162e5451a629983ef2130a1d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Возвращает элемент массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwIndex`  
 [in] Индекс элемента.  
  
 `ppElement`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс, представляющий элемент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод видит все элементы объекта массива как одномерный массив, даже если объект array является многомерным. Например, если массив `myarray[3][2][6]` и `dwIndex` параметра равным 20, этот метод возвращает элемент из `myarray[1][1][2]`и `dwIndex` параметр 21 вернет элемент из `myarray[1][1][3]`. Используйте [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) метод, чтобы определить общее число элементов в массиве.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)