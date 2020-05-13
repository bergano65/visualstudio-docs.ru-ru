---
title: IDebugProgramHost2::GetHostName Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722228"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Получает название, дружеское имя или название файла процесса хостинга этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Параметры
`dwType`\
(в) Значение из [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) перечисления.

`pbstrHostName`\
(ваут) Возвращает запрашиваемое название процесса хостинга.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 В типичной реализации этого `dwType` метода параметр игнорируется и возвращается дружественное имя хост-машины. Другой возможной реализацией `dwType` является передача параметра на вызов методу [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) для получения имени.

## <a name="see-also"></a>См. также
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
