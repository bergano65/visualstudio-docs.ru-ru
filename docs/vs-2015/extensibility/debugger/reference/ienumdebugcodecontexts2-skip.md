---
title: IEnumDebugCodeContexts2::Skip | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Skip
helpviewer_keywords:
- IEnumDebugCodeContexts2::Skip
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abf8ea0b14f1afdda3d950127ca814993c29eea1
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62551609"
---
# <a name="ienumdebugcodecontexts2skip"></a>IEnumDebugCodeContexts2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Пропускает заданное число элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество пропускаемых элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если `celt` больше, чем число оставшихся элементов; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если `celt` указывает значения, большего, чем остальных элементов, перечислению задается до конца и `S_FALSE` возвращается.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
