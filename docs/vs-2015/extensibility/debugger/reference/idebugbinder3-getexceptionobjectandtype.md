---
title: IDebugBinder3::GetExceptionObjectAndType | Документация Майкрософт
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
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd25f471372b8102e9d730af09d496b4799ceeff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827328"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает исключение, связанное с объектом, если таковые имеются.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppException`  
 [out] Возвращает объект, представляющий исключение.  
  
 `ppField`  
 [out] Возвращает объект, представляющий определенного поля, которое вызвало исключение (это может быть значение null).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Чтобы проверить, имеется ли исключение, проверьте значение, возвращаемое `ppException`: если он имеет значение null, то исключение не связан с данным объектом.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

