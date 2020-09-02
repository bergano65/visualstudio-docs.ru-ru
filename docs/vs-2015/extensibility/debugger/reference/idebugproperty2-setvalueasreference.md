---
title: 'IDebugProperty2:: Сетвалуеасреференце | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a94e3767ee05e39e847af27dc5999fa8bbbe2d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193449"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присваивает этому свойству значение, равное заданной ссылке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Массив аргументов, передаваемый методу задания свойств управляемого кода. Если метод задания свойств не принимает аргументы или этот объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) не ссылается на такой метод задания свойства, то `rgpArgs` должен иметь значение null. Обычно этот параметр имеет значение null.  
  
 `dwArgCount`  
 окне Число аргументов в `rgpArgs` массиве.  
  
 `pValue`  
 окне Ссылка в виде объекта [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) на значение, используемое для задания этого свойства.  
  
 `dwTimeout`  
 окне Время, затрачиваемое на задание значения (в миллисекундах). Типичное значение — `INFINITE` . Это влияет на время, в течение которого может выполняться любая возможная оценка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки, обычно один из следующих:  
  
|Ошибка|Описание|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Установка значения из ссылки не поддерживается.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Значение не может быть задано, так как это свойство ссылается на метод.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Значение доступно только для чтения и не может быть задано.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
