---
title: 'IDebugProgramHost2:: @ HostName | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722228"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Возвращает заголовок, понятное имя или имя файла ведущего процесса этой программы.

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
окне Значение из перечисления [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .

`pbstrHostName`\
заполняет Возвращает запрошенное имя ведущего процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 В обычной реализации этого метода `dwType` параметр игнорируется, и возвращается понятное имя хост-компьютера. Другой возможной реализацией является передача `dwType` параметра в вызов метода- [HostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) для получения имени.

## <a name="see-also"></a>См. также раздел
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
