---
title: IDebugProperty3::D Естройобжектид | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a610cd5c947d77048e86b31c92298f6cc18607d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193423"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Уничтожает уникальный идентификатор, связанный с этим свойством, который указывает, что вызывающий объект более не должен идентифицировать это свойство, уникально на основе всех остальных свойств.  
  
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
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если модулю отладки не требуется поддерживать уникальные идентификаторы для свойства (поскольку он уже отслеживает их уникальным образом), то он может просто вернуться `E_NOTIMPL` для этого метода.  
  
 Уникальные идентификаторы создаются с помощью вызова метода [креатеобжектид](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) , когда вызывающему объекту нужно убедиться, что это свойство однозначно идентифицируется всеми другими свойствами.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
