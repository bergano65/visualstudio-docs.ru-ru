---
title: IEnumDebugAddresses::Reset | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866c96f81edd5406f36790b932b057f6279f7e67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992643"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод выполняет сброс перечисления к первому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
