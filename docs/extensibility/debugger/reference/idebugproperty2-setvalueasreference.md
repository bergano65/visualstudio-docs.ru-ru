---
title: "IDebugProperty2::SetValueAsReference | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsReference
helpviewer_keywords: IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d27a087c67401e90e8a3f4629c27d1255d0ade75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Устанавливает значение этого свойства равным данной ссылки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rgpArgs`  
 [in] Массив аргументов для передачи методу задания свойства управляемого кода. Если метод задания свойства не принимает аргументы или если этот [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект не ссылается на такой метод задания свойства, `rgpArgs` должен иметь значение null. Как правило, этот параметр имеет значение null.  
  
 `dwArgCount`  
 [in] Число аргументов в `rgpArgs` массива.  
  
 `pValue`  
 [in] Справочник, в виде [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта, чтобы значение, используемое для установки этого свойства.  
  
 `dwTimeout`  
 [in] Сколько времени необходимо выполнить, чтобы задать значение, в миллисекундах. Обычно значение `INFINITE`. Это влияет на продолжительность времени, которые могут использовать все возможности оценки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает ошибку кода, обычно один из следующих:  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Установка значения из ссылки не поддерживается.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Значение не может быть установлен, поскольку это свойство ссылается на метод.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Значение доступно только для чтения и не может быть задано.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)