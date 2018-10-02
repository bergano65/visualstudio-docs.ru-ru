---
title: IDebugPointerObject::SetBytes | Документация Майкрософт
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
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48f5ffc38b83e227b35ac3967f06baa36f43b839
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572326"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPointerObject::SetBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject-setbytes).  
  
Задает значение, на который он указывает серию последовательных байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwStart`  
 [in] Указывает смещение в байтах от начала объекта.  
  
 `dwCount`  
 [in] Число байтов для задания.  
  
 `pBytes`  
 [in] Массив байтов, представляющий новое значение. Это значение хранится в объекте, начиная с заданного смещения.  
  
 `pdwBytes`  
 [out] Возвращает число байтов, фактически задания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется в том случае, если указатель, представленного этим объектом [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) указывает на тип-примитив или простого массива типов-примитивов (то есть массив, могут быть представлены простые последовательности байтов). Это `IDebugPointerObject` объект не может быть пустая ссылка (оно должно указывать на адрес в памяти).  
  
## <a name="see-also"></a>См. также  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

