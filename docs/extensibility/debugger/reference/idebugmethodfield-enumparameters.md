---
title: IDebugMethodField::EnumParameters | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 674f2cc7160ace49f4fc8b5333fc3b951a7ccc8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823183"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Создает перечислитель для параметров метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParams`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список параметров метода; в противном случае возвращает значение null, если параметров нет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если параметров нет. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент является [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект, представляющий различные типы параметров. Вызовите [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) метод для каждого объекта, чтобы определить точно какого рода параметр представляет объект.  
  
 Параметр включает в себя, как его имя переменной, так и его тип. Первый параметр метода класса обычно является указатель «this».  
  
 Если только типы параметров требуется, вызовите [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)