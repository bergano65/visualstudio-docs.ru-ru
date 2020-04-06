---
title: IDebugCoreServer3:CreateInstanceServer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2346bb76fe604265a309a51f48b734fc6f2ab8d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733017"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Создает экземпляр отладки двигателя на сервере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Параметры
`szDll`\
(в) Путь к dll, который реализует CLSID, указанный в параметре. `clsidObject` Если это `NULL`так, то `CoCreateInstance` функция COM называется.

`wLangId`\
(в) Локаль двигателя отладки. Это может быть 0, если метод [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) не должен быть вызван.

`clsidObject`\
(в) CLSID отладки двигателя для создания.

`riid`\
(в) Идентификатор интерфейса конкретного интерфейса для извлечения из объекта класса.

`ppvObject`\
(ваут) `IUnknown` интерфейс от мгновенного объекта. Влите или маршал этот объект к желаемому интерфейсу.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
