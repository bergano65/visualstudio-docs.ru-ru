---
title: IDebugArrayObject::GetCount | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 00f3f0daa09f41168224c0d0817707de26dc817a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Получает число элементов в массиве.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwElements`  
 [out] Возвращает число.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод видит все элементы объекта массива как одномерный массив, даже если объект array является многомерным. Например, если массив `myarray[3][2][6]`, этот метод вернет 36 в `pdwElements` параметра. Используйте [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) метод для извлечения отдельных элементов одной за раз.  
  
## <a name="see-also"></a>См. также  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)