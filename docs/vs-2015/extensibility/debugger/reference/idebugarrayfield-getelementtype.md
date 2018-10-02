---
title: IDebugArrayField::GetElementType | Документация Майкрософт
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
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae308366c9a782c453402f5e04eebe5c6a4a5dd3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562913"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugArrayField::GetElementType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayfield-getelementtype).  
  
Получает тип элемента в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppType`  
 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , описывающий тип элемента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) объект предполагает, что все элементы массива относятся к одному типу.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

