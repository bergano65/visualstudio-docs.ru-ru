---
title: IDebugProcess2::Detach | Документация Майкрософт
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
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1895c146f557e0c3ba79bd84970b99fc663cc891
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564028"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcess2::Detach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-detach).  
  
Отсоединяет отладчика от этого процесса путем отсоединения всех программ в процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Все программы и процесс продолжать работать, но больше не являются частью сеанса отладки. После отсоединения операции завершения, не более отладки, которые будут отправляться события для этого процесса (и его программы).  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

