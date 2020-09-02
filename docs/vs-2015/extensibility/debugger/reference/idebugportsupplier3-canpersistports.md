---
title: 'IDebugPortSupplier3:: Канперсистпортс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188183"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод определяет, может ли поставщик порта сохранять порты (путем записи на диск) между вызовами отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `S_OK` Если порты можно сохранить или `S_FALSE` указать, что порты не могут быть сохранены.  
  
## <a name="remarks"></a>Remarks  
 Если поставщик порта может сохранять порты, он должен сделать это, когда он будет уничтожен, а затем перезагрузить его при повторном создании экземпляра.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
