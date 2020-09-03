---
title: 'IDebugFunctionObject2:: Evaluate | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c25e62dbfc0778fb1bf07c9108c9111f3520d87f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180968"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Вызывает функцию и возвращает результирующее значение в виде объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParams`  
 окне Массив объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющих входные параметры. Каждый из этих параметров был создан с помощью одного из методов create в этом интерфейсе.  
  
 `dwParams`  
 окне Число параметров в `ppParams` массиве.  
  
 `dwEvalFlags`  
 окне Сочетание флагов из перечисления [евалфлагс](../../../extensibility/debugger/reference/evalflags.md) , определяющее способ выполнения вычисления.  
  
 `dwTimeout`  
 окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте **бесконечность** для бесконечного ожидания.  
  
 `ppResult`  
 заполняет Возвращает объект **идебугобжект** , представляющий значение функции в виде объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
