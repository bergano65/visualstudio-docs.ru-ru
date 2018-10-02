---
title: IDebugProgram2::GetDebugProperty | Документация Майкрософт
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
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e92d0a20fb9639e3a969ff30a5b6b512019895a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557647"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgram2::GetDebugProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getdebugproperty).  
  
Возвращает свойства программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProperty`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойства программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Свойства, возвращаемые этим методом относятся только к программе. Если программе необходимо вернуть более одного свойства, то [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта, возвращаемого этим методом является контейнером дополнительных свойств и вызова метода [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает метод список всех свойств.  
  
 Программы могут предоставлять любое количество и тип дополнительных свойств, которые могут быть описаны до `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать свойства дополнительные программы через пользовательский интерфейс браузера универсальное свойство.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

