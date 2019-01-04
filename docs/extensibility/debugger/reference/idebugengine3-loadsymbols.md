---
title: IDebugEngine3::LoadSymbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b74b4303d85364e5d6afa2eb0618c32770ac3a23
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865158"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Загружает (при необходимости) символы для всех модулей, отладку этого ядро отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это загружает отладочные символы для всех модулей, которые ссылается это ядро отладки. Символы загружаются только в том случае, если они еще не загружен. Символы производится поиск по путям, заданный вызовом к [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>См. также  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)