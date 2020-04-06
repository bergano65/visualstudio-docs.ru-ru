---
title: IDebugProperty2::GetExtendedInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721490"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Получает расширенную информацию для отеля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>Параметры
`guidExtendedInfo`\
(в) GUID определяет тип расширенной информации, подхваченной. Дополнительные сведения см. в разделе "Примечания".

`pExtendedInfo`\
(ваут) Возвращает `VARIANT` (СЗ) или объект (СЗ), который может быть использован для получения расширенной информации о свойстве. Например, этот параметр `IUnknown` может вернуть интерфейс, который может быть запрошен для интерфейса [IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Дополнительные сведения см. в разделе "Примечания".

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки. Возвращает, `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` если нет расширенной информации для получения.

## <a name="remarks"></a>Примечания
 Этот метод существует с целью извлечения информации, которая не поддается извлечению, позвонив в метод [GetPropertyInfo.](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

 Следующие GUID, как правило, распознаются этим методом (значения GUID указаны для C, так как имя не доступно ни в одной сборке). Дополнительные GUID могут быть созданы для внутреннего использования.

|name|GUID|Описание|
|----------|----------|-----------------|
|guidДокумент|3f98de84-fee9-11d0-b47f-00a0244a1dd2|Возвращает `IUnknown` интерфейс в документ. Как правило, интерфейс [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) можно `IUnknown` получить из этого интерфейса.|
|guidCodeКонтекст|(e2fc65e-56ce-11d1-b528-00aax004a8797)|Возвращает `IUnknown` интерфейс в контекст документа. Как правило, интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) можно `IUnknown` получить из этого интерфейса.|
|guidCustomViewerПоддерживаето|(d9c9da31-ffbe-4eeb-9186-23121e3c088c)|Возвращает строку, содержащую CLSID пользовательского просмотра, обычно реализуемую оценщиком выражения.|
|guidExtendedInfoSlot|6df235ad-82c6-4292-9c97-7389770bc42f|Возвращает 32-битный номер, представляющий нужный номер слота, если это свойство представляет собой локальный адрес управляемого кода.|
|guidExtendedInfoSignature|(b5fb6d46-f805-417f-96a3-8ba737073ffd)|Возвращает строку, содержащую подпись переменной, связанной с объектом свойства.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
