---
title: IDebugProgram2::CanDetach | Документация Майкрософт
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
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa0b352b563365606f20d0094974b52a7e4a7926
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568282"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProgram2::CanDetach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-candetach).  
  
Определяет, если отладчик (DE) можно отсоединить от программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если можно будет отсоединить, возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_FALSE` Если DE не удается отсоединиться от программы.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

