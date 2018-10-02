---
title: IDebugProperty3::DestroyObjectID | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 012a4fcc8b5ada9208a3d2b4cd65e5e7ae5c225d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558784"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProperty3::DestroyObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-destroyobjectid).  
  
Уничтожает уникальный идентификатор, связанный с этим свойством, указывающее, что вызывающий объект больше не волнует для определения этого свойства уникально от всех других свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если модуль отладки не требуется для поддержки уникальных идентификаторов для свойства (так как он уже отслеживает их однозначно внутренне), а затем может просто вернуть `E_NOTIMPL` для этого метода.  
  
 Уникальные идентификаторы, созданные с помощью вызова [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) метод, когда вызывающий объект хочет убедиться, что это свойство однозначно идентифицируется среди всех остальных свойств.  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)

