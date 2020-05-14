---
title: IDebugProgramProvider2::GetProviderProgramNode Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721802"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Извлекает узла программы для конкретной программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Параметры
`Flags`\
(в) Сочетание флагов из [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) перечисления. Для этого вызова характерны следующие флаги:

|Флаг|Описание|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Звонящий работает на удаленной машине.|
|`PFLAG_DEBUGGEE`|В настоящее время вызыватель отлажается (дополнительная информация о сборе будет возвращена для каждого узла).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Звонящее было прикреплено к отладчику, но не запущено.|

`pPort`\
(в) Порт, в котором работает процесс вызова.

`processId`\
(в) [Структура AD_PROCESS_ID,](../../../extensibility/debugger/reference/ad-process-id.md) держащая идентификатор процесса, содержащего данную программу.

`guidEngine`\
(в) GUID отладки двигателя, что программа прилагается к (если таковые имеется).

`programId`\
(в) Идентификатор программы, для которого можно получить узла программы.

`ppProgramNode`\
(ваут) Объект [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) представляющий запрашиваемый узла программы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
