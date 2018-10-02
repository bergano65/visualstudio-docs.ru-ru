---
title: IDebugExpressionContext2::GetName | Документация Майкрософт
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
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62faff603e60340063eb6bd8f0eb60ad82c839c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562579"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExpressionContext2::GetName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressioncontext2-getname).  
  
Извлекает имя в контекст оценки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 [out] Возвращает имя контекста вычисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Имя — это описание этого контекста вычисления. Она обычно является то, что может быть проанализирован вычислитель выражений, который ссылается на этот контекст точные оценки. Например в C++ имя выглядит следующим образом:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)

