---
title: "IDebugProgram2::CanDetach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 6508286e277eb72dd9f0cb0810146dccd8ec59ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Определяет, если в программе можно отсоединить отладчик (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если можно отсоединить, а возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `S_FALSE` Если DE не удается отсоединиться от программы.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
