---
title: Предоставление автоматизации для кода | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724966"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не является обязательным. Пакет SDK для среды не предоставляет пример для этого. Подробные сведения о моделях кода см. в разделе объект <xref:EnvDTE.CodeModel>.

 Для реализации модели кода необходимо реализовать все интерфейсы, определяемые внутренней структурой данных. Объекты должны быть производными от класса `IDispatch`.

 Объекты, которые расширяются, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel>, доступны в объекте <xref:EnvDTE.Project> и выглядят следующим образом:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Можно выбрать реализацию только `CodeModel` или интерфейса `FileCodeModel` в объекте, возвращаемом из объектов `Project` и <xref:EnvDTE.ProjectItem>. Предоставьте все функциональные возможности этого интерфейса, которые подходят для вашей системы проектов.

 Если вы хотите добавить такие компоненты, как методы или свойства, которые недоступны из стандартных `CodeModel` и `FileCodeModel` интерфейсов, создайте собственный интерфейс, наследующий от стандартного. Не забудьте задокументировать его в системе проекта, чтобы конечные пользователи могли найти его. Вы возвращаете стандартный интерфейс, но пользователь может вызвать метод `QueryInterface` или выполнить приведение к интерфейсу, если известно, что он существует.

## <a name="see-also"></a>См. также
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)