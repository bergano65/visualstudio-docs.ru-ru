---
title: IDebugProperty3::DestroyObjectID | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e6679c35452c63009046afb275922188d4fede6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916359"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Уничтожает уникальный идентификатор, связанный с этим свойством, указывающее, что вызывающий объект больше не волнует для определения этого свойства уникально от всех других свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если модуль отладки не требуется для поддержки уникальных идентификаторов для свойства (так как он уже отслеживает их однозначно внутренне), а затем может просто вернуть `E_NOTIMPL` для этого метода.  
  
 Уникальные идентификаторы, созданные с помощью вызова [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) метод, когда вызывающий объект хочет убедиться, что это свойство однозначно идентифицируется среди всех остальных свойств.  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)