---
title: 'IDebugEngine2:: Каусебреак | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731164"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Запрашивает, что все программы, отлаживаемых с помощью этого модуля отладки (DE), останавливают выполнение при следующем попытке запуска одного из их потоков.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод является асинхронным: событие [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) отправляется при следующей попытке выполнения программы после вызова этого метода.

## <a name="see-also"></a>См. также раздел
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
