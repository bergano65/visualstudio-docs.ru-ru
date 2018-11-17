---
title: IDebugFunctionObject2::CreateObject | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64b6c069abe04f25e7aa82b579cf4d905686dcf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770518"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает объект, который использует конструктор параметров флаг вычисления и значение времени ожидания.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pConstructor`  
 [in] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , представляющий конструктор объекта должен быть создан.  
  
 `dwArgs`  
 [in] Число параметров в `pArg` массива. Представляет число параметров, переданных конструктору.  
  
 `pArgs`  
 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, которые представляют параметры передается конструктору.  
  
 `dwEvalFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, каким образом будет осуществляться вычисления.  
  
 `dwTimeout`  
 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте **БЕСКОНЕЧНЫЙ** для неограниченного времени ожидания.  
  
 `ppObject`  
 [out] Возвращает **IDebugObject** представляющий только что созданный объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса или других сложный тип, который требуется конструктор, который является параметром.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)

