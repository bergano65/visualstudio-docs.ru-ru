---
title: IDebugProperty2::SetValueAsString | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5fb55fb6f9a90cf39120be408428524f64463d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Задает значение свойства из заданной строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszValue`  
 [in] Строка, содержащая задаваемое значение.  
  
 `nRadix`  
 [in] Основание системы счисления для использования в интерпретации все числовые данные. Это может быть 0, чтобы попытаться автоматически определить основание системы счисления.  
  
 `dwTimeout`  
 [in] Указывает максимальное время (в миллисекундах) ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие возможные значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Строка не может быть преобразовано в значение свойства или не удалось задать значение свойства.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Свойство доступно только для чтения.|  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)