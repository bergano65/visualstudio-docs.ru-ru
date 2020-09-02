---
title: 'IDebugProgram2:: Жетдебугпроперти | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b86a1aa144e553b126445a865330a8edb786ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187903"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойства программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Свойства, возвращаемые этим методом, относятся только к программе. Если программе необходимо вернуть более одного свойства, то объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , возвращаемый этим методом, является контейнером дополнительных свойств и вызовом метода [енумчилдрен](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) возвращает список всех свойств.  
  
 Программа может предоставлять любое количество и тип дополнительных свойств, которые можно описать через `IDebugProperty2` интерфейс. Интегрированная среда разработки может отображать дополнительные свойства программы через пользовательский интерфейс обозревателя универсальных свойств.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
