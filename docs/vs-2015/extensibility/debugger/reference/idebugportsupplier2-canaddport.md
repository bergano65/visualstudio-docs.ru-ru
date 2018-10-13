---
title: IDebugPortSupplier2::CanAddPort | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: db45b66ee47a22aff9c3dfca944a4524450df607
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244391"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

