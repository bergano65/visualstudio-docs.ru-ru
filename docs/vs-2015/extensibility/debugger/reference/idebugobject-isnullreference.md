---
title: IDebugObject::IsNullReference | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd116b236eb57e2fab638cfaa8412167a6d1180f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188894"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Проверяет, является ли этот объект является пустой ссылкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsNull`  
 [out] Возвращает ненулевое значение (`TRUE`) Если этот объект является пустой ссылкой; в противном случае возвращает 0 (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Ссылку на null означает, что пустой объект или объект, который не был назначен.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
