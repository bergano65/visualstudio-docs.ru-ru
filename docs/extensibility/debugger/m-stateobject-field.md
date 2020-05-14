---
title: поле m_stateObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738369"
---
# <a name="m_stateobject-field"></a>m_stateObject поле
Объект, представляющий данные, которые будет использоваться в действии.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Поскольку вы не можете получить доступ к этому внутреннему члену из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Примечания
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструкторе. Это также резервное поле <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> для собственности.

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
