---
title: "IDebugClassField::EnumInterfacesImplemented | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e185c6ba5d51332396670798df963b3f2612e33a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Создает перечислитель для интерфейсов, реализуемых данным классом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список интерфейсов, реализованных. Возвращает значение null в случае отсутствия интерфейсов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK, или возвращает S_FALSE, если нет интерфейсы, реализованные в этом классе. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент перечисления является [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, описывающий интерфейс. Обратите внимание, что неуправляемый [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] код не использует интерфейсы как отдельная сущность, этот метод всегда возвращает значение null для неуправляемого [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] кода.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
