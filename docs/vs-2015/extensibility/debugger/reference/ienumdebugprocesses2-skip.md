---
title: IEnumDebugProcesses2::Skip | Документация Майкрософт
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
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9473af008e6f50d6f5917da362ffb5c0cdfba499
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761209"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
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
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если `celt` больше, чем число оставшихся элементов; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если `celt` указывает значения, большего, чем остальных элементов, перечислению задается до конца и `S_FALSE` возвращается.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)

