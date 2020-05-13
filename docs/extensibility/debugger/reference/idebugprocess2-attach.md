---
title: IDebugПроцесс2::Прикрепите Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724196"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Прикрепляет к процессу менеджер отладки сеанса (SDM).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) используемый для уведомления о событиях.

`rgguidSpecificEngines`\
(в) Массив GUIDs отладок двигателей, которые будут использоваться для отладки программ, работающих в этом процессе. Этот параметр может быть нулевая величина. Дополнительные сведения см. в разделе "Примечания".

`celtSpecificEngines`\
(в) Количество отладок двигателей `rgguidSpecificEngines` в массиве `rghrEngineAttach` и размер массива.

`rghrEngineAttach`\
(в, вне) Массив кодов HRESULT, возвращенных двигателями отладки. Размер этого массива указан `celtSpecificEngines` в параметре. Каждый код, `S_OK` `S_ATTACH_DEFERRED`как правило, либо . Последний указывает на то, что DE в настоящее время прилагается к программам.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.

|Значение|Описание|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанный процесс уже подключен к отладчику.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Нарушение безопасности произошло во время процедуры присоединения.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Процесс рабочего стола не может быть прикреплен к отладчику.|

## <a name="remarks"></a>Примечания
 Присоединение к процессу прикрепляет SDM ко всем программам, работающим в этом процессе, которые `rgguidSpecificEngines` могут быть отдипированы двигателями отладки (DE), указанными в массиве. Установите `rgguidSpecificEngines` параметр на нулевую величину или включите `GUID_NULL` в массив, чтобы прикрепить ко всем программам в процессе.

 Все события отладки, возникающие в процессе, отправляются на данный объект [IDebugEventCallback2.](../../../extensibility/debugger/reference/idebugeventcallback2.md) Этот `IDebugEventCallback2` объект предоставляется при вызове этого метода SDM.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
