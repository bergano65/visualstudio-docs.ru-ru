---
title: IDebugPortSupplier3::EnumPersistedPorts | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c29e53df99c019f0b50a1dcd13c7c74280025ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876946"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Этот метод извлекает объект, позволяющий перечисления из списка сохраненных портов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `PortNames`  
 [in] Объект [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) структура, содержащая список имен портов для поиска и возврата материализованных портов. Будут возвращены только порты, сохраненные с этими именами.  
  
 `ppEnum`  
 [out] Объект, реализующий [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сохраненные порты загружаются при создании экземпляра поставщика порта и сохранить при уничтожении поставщика порта.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)