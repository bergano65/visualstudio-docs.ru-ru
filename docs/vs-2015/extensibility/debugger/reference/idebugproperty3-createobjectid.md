---
title: IDebugProperty3::CreateObjectID | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e27d0dca73829bb5dd98c42d2e42ba34f4afdf0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776204"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает уникальный идентификатор для этого свойства, чтобы убедиться, что он является уникальным среди всех остальных свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается, когда диспетчер отладки сеансов хочет убедиться, что это свойство однозначно идентифицируется среди всех остальных свойств. Модуль отладки (DE) поддерживает этот метод, если только свойства, которые он имеет дело с уже однозначно идентифицируются. Если DE не поддерживает этот метод, он возвращает `E_NOTIMPL`.  
  
 Любой уникальный идентификатор, созданный с помощью `CreateObjectID` при уничтожении [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) вызывается метод; это также означает конец необходимость для уникальной идентификации этого свойства.  
  
> [!NOTE]
>  Нет метода для получения этот уникальный идентификатор, поэтому DE можно выполнять необходимые элементы для уникальных идентификаторов при `CreateObjectID` вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

