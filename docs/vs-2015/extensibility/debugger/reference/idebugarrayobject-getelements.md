---
title: 'Идебугаррайобжект:: @ Elements | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cad81d76e2fcec01fa50a37fa6ab6cb49cfc79be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423703"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает перечислитель всех элементов массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 заполняет Возвращает объект [иенумдебугобжектс](../../../extensibility/debugger/reference/ienumdebugobjects.md) , позволяющий перечислять все элементы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В качестве альтернативы можно использовать методы [NOCOUNT](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) и- [элемента](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) для выполнения итерации по элементам.  
  
## <a name="see-also"></a>См. также:  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
