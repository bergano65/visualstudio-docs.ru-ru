---
title: IDebugProgramProvider2:GetProviderProcessData Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721854"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Извлекает список запущенных программ из заданного процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|Абонент просит вернуть список узлов программы.|

`pPort`\
(в) Порт, в котором работает процесс вызова.

`processId`\
(в) [Структура AD_PROCESS_ID,](../../../extensibility/debugger/reference/ad-process-id.md) держащая идентификатор процесса, содержащего данную программу.

`EngineFilter`\
(в) Массив GUID для отладки двигателей, назначенных для отладки этого процесса (они будут использоваться для фильтрации программ, которые фактически возвращаются на основе того, что поставляемые двигатели поддержки; если двигатели не указаны, то все программы будут возвращены).

`pProcess`\
(ваут) [Структура PROVIDER_PROCESS_DATA,](../../../extensibility/debugger/reference/provider-process-data.md) заполненная запрашиваемым сведениями.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод обычно вызывается процессом для получения списка программ, работающих в этом процессе. Возвращенная информация представляет собой список объектов [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>См. также
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
