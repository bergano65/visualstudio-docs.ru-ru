---
title: m_stateObject поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c49682d43236f66b3acbef630f1d81b32e97dab2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889496"
---
# <a name="mstateobject-field"></a>поле m_stateObject
Объект, представляющий данные, которые будет использовать действие.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Примечания
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструктор. Это также резервное поле для <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> свойство.

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)