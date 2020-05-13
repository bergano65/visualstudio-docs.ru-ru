---
title: IDebugClassField::DoesInterfaceExist Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734495"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Определяется, определяется ли определенный интерфейс в классе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Параметры
`pszInterfaceName`\
(в) Строка, содержащая имя интерфейса для поиска.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращает S_OK, возвращает S_FALSE, если интерфейс не существует; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод фактически получает перечисление всех интерфейсов и выполняет поиск по списку для соответствующего интерфейса.

## <a name="see-also"></a>См. также
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
