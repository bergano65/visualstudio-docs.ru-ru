---
title: поле m_children Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738426"
---
# <a name="m_children-field"></a>m_children поле
Список детских задач, зарегистрированных с этой задачей.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Поскольку вы не можете получить доступ к этому внутреннему члену из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Примечания
 В то время как задача выполняется, только поток, выполняемый задачей, должен получить доступ к этому массиву.

 Если задача выполнена, другие потоки могут получить доступ к этому полю до тех пор, пока они ничего не добавят к нему или удалит что-либо из него.

## <a name="see-also"></a>См. также
- [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
