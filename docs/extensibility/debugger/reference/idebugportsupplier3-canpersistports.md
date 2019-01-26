---
title: IDebugPortSupplier3::CanPersistPorts | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78d66f9d267745c1e39c7fc007680009f8881eb4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933793"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Этот метод определяет ли поставщик порта может сохранять данные порты (при их записи на диск) между вызовами отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `S_OK` Если порты могут сохраняться, или `S_FALSE` для указания, что порты не могут быть сохранены.  
  
## <a name="remarks"></a>Примечания  
 Если поставщика порта можно сохранить порты, его следует сделать это, когда он будет уничтожен и затем загружает их повторно при создании еще раз для экземпляра.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)