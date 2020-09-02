---
title: 'IEnumDebugThreads2:: Clone | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9732942234f896216031d74acd5143832049bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147741"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает копию текущего перечисления как отдельный объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает копию этого перечисления как отдельный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Копия перечисления имеет то же состояние, что и оригинал, во время вызова этого метода. Однако исходное состояние копии и исходного состояния является отдельным и может быть изменено по отдельности.  
  
## <a name="see-also"></a>См. также:  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
