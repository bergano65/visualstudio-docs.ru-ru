---
title: 'Идебугфиелд:: Contain | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1217a6f3a62f331fa09d9ed276640ef62cca8d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728905"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Этот метод возвращает контейнер поля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Параметры
`ppContainerField`\
заполняет Возвращает контейнер, представленный интерфейсом [идебугконтаинерфиелд](../../../extensibility/debugger/reference/idebugcontainerfield.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если в этом поле нет контейнера, возвращается `ppContainerField` значение null.

## <a name="see-also"></a>См. также раздел
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
