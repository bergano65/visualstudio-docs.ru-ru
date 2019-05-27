---
title: IDebugProperty2::GetExtendedInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d9e2ff4b853baec5da19b4c62cffe4e86102736
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211604"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Возвращает расширенные сведения для свойства.

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
[in] Идентификатор GUID, который определяет тип расширенные сведения, которые требуется извлечь. Дополнительные сведения см. примечания.

`pExtendedInfo`\
[out] Возвращает `VARIANT` (C++) или объект (C#), можно использовать для получения этих данных расширенного свойства. Например, этот параметр может возвращать `IUnknown` интерфейс, который можно запросить для [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс. Дополнительные сведения см. примечания.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Если нет для получения расширенной информации.

## <a name="remarks"></a>Примечания
 Этот метод используется для получения данных, которые не совместима получить, вызвав [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод.

 Следующие идентификаторы GUID обычно распознаются этим методом, (значения GUID задаются для C#, так как имя недоступно в любой сборке). Можно создать дополнительные идентификаторы GUID для внутреннего использования.

|name|Идентификатор GUID|Описание|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Возвращает `IUnknown` интерфейс к документу. Как правило [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) интерфейс может быть получен из этого `IUnknown` интерфейс.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Возвращает `IUnknown` интерфейс к контексту документа. Как правило [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейс может быть получен из этого `IUnknown` интерфейс.|
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Возвращает строку, содержащую идентификатор CLSID пользовательское средство просмотра, обычно реализуют вычислитель выражений.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Возвращает 32-разрядное число, представляющее номер нужного слота, если это свойство представляет локальный адрес управляемого кода.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Возвращает строку, содержащую сигнатуру переменная, связанная с объект свойства.|

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)