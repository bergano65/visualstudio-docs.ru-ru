---
title: IDebugBreakpointChecksumRequest2::IsChecksumEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::IsChecksumEnabled
ms.assetid: 8b1853b5-745c-4cd6-88a9-ce0673971bb0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec878a08e6f22a461eee95f31db7fa2a1bc97886
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62431567"
---
# <a name="idebugbreakpointchecksumrequest2ischecksumenabled"></a>IDebugBreakpointChecksumRequest2::IsChecksumEnabled
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, включен ли контрольная сумма для этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsChecksumEnabled(   
   BOOL *pfChecksumEnabled  
);  
```  
  
```csharp  
public int IsChecksumEnabled(   
   out int pfChecksumEnabled  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfChecksumEnabled`  
 [out] Возвращает значение TRUE, если включена контрольная сумма; в противном случае возвращает значение FALSE.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
