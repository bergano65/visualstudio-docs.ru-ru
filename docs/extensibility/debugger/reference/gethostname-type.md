---
title: GETHOSTNAME_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f158cdaba17c030ce830c8adf26b6985c9b86dad
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413441"
---
# <a name="gethostnametype"></a>GETHOSTNAME_TYPE
Указывает тип имени узла.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="members"></a>Участники
GHN_FRIENDLY_NAME  
Указывает понятное имя узла.

GHN_FILE_NAME  
Указывает имя файла узла.

## <a name="remarks"></a>Примечания
Эти значения передаются в качестве аргумента [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) метод для извлечения имени узла в различных форматах.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
