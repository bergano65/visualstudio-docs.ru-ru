---
title: IDebugBinder3::GetEEService Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735829"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Этот метод возвращает запрашиваемую службу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Параметры
`vendor`\
(в) `GUID` поставщика (нулевая стоимость приемлема).

`language`\
(в) `GUID` языка (нулевая стоимость приемлема).

`iid`\
(в) `IID` услуги для получения.

`ppService`\
(ваут) Интерфейс запрашиваемый сервис.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Передайте `IID` для [iEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) `IID_IEEVisualizerServiceProvider`интерфейс ( ), чтобы увидеть, если тип Визуализатор услуга доступна. Если это так, то оценщик экспрессии может получить интерфейс [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) для поддержки визуализаторов типов. Подробности смотрите [визуализационные и просматриваемые данные.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
