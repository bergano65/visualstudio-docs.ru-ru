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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bb7d89128ce5c2002d38f18bf7b93f74817191b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985319"
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