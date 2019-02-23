---
title: Поля m_children | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fefeaf07c923a5fefa282efcd96948b2d907cca1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704648"
---
# <a name="mchildren-field"></a>m_children field
Список дочерних задач, которые зарегистрированы с помощью этой задачи.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Примечания
 Пока выполняется задача, только потоку, который выполняет задачу должен получить доступ к этот массив.

 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не ничего добавлять к нему или удалить любой элемент из него.

## <a name="see-also"></a>См. также
- [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)