---
title: 'Внутренние элементы: класс ContingentProperties | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7b9775ed74e7ae81768f180e596f171b2c99cba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344322"
---
# <a name="contingentproperties-class---internal-members"></a>Внутренние элементы: класс ContingentProperties
Содержит дополнительные свойства для <xref:System.Threading.Tasks.Task> объекта.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как при отсутствии доступа к этим внутренним членам платформы .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Участники

### <a name="fields"></a>Поля

|name|Описание|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Список дочерних задач, которые зарегистрированы с помощью этой задачи.|

## <a name="remarks"></a>Примечания
 .NET Framework инициализирует поля этого класса, только в том случае, когда они нужны.

## <a name="see-also"></a>См. также
- [Внутренние компоненты параллельных расширений для .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)