---
title: IDebugPortSupplier2::CanAddPort | Документация Майкрософт
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
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1478841e6fdd48a6c956486153db7bf4e81435fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557819"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPortSupplier2::CanAddPort](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier2-canaddport).  
  
Проверяет, что поставщик порта можно добавить новые порты.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Можно ли добавить порт, возвращает `S_OK`; в противном случае возвращает `S_FALSE` для указания порты не могут добавляться к этого поставщика порта.  
  
## <a name="remarks"></a>Примечания  
 Вызовите этот метод перед вызовом [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) метод, так как последний метод создает порт, а также добавление, которая может оказаться длительной операции.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

