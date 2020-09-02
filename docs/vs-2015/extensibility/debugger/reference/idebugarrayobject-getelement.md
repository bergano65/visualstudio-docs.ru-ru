---
title: 'Идебугаррайобжект:: элемент | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423690"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает элемент массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Индекс элемента.  
  
 `ppElement`  
 заполняет Возвращает интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий элемент.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод видит все элементы объекта массива в виде одномерного массива, даже если объект массива является многомерным. Например, при наличии массива `myarray[3][2][6]` и `dwIndex` параметра 20 этот метод возвратит элемент из `myarray[1][1][2]` , а `dwIndex` параметр, равный 21, возвратит элемент из `myarray[1][1][3]` . Используйте метод [NOCOUNT](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) , чтобы определить общее число элементов в массиве.  
  
## <a name="see-also"></a>См. также:  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
