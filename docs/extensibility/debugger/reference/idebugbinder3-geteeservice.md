---
title: 'IDebugBinder3:: Жетисервице | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5156f905eb5891be64d0718e8aeff4c3c404663b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891258"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Этот метод возвращает запрошенную службу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Параметры
`vendor`\
[входные] `GUID` поставщика (значение NULL приемлемо).

`language`\
[входные] `GUID` языка (значение NULL допустимо).

`iid`\
[входные] `IID` получаемой службы.

`ppService`\
заполняет Интерфейс для запрошенной службы.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Передайте значение `IID` для интерфейса [иивисуализерсервицепровидер](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ), чтобы узнать, доступна ли служба визуализатора типов. Если это так, средство оценки выражений может получить интерфейс [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) для поддержки визуализаторов типов. Дополнительные сведения см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
