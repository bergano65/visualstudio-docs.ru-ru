---
title: 'IDebugProgramPublisher2:: Унпублишпрограм | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3841ba0698c5e63bbf58e47e0e4a8b8f75d068e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961215"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Делает программу недоступной для отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Параметры
`pDebuggeeInterface`\
окне `IUnknown` Интерфейс программы. Это то же значение, которое передается в метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) и уникально идентифицирует удаляемую программу (то есть она используется как файл cookie).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Чтобы сделать программу доступной для модулей отладки и диспетчера отладки сеансов, используйте метод [публишпрограм](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
