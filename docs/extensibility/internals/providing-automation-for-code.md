---
title: Предоставление автоматизации для кода | Документация Майкрософт
description: Сведения о реализации модели кода, которая требует реализации интерфейсов, определяемых внутренней структурой данных.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8d0745ae971f4039ffccf3431614325236e63f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875860"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не является обязательным. Пакет SDK для среды не предоставляет пример для этого. Подробные сведения о моделях кода см. в разделе <xref:EnvDTE.CodeModel> объект.

 Для реализации модели кода необходимо реализовать все интерфейсы, определяемые внутренней структурой данных. Объекты должны быть производными от `IDispatch` класса.

 Объекты, которые вы расширяете, <xref:EnvDTE.CodeModel> и <xref:EnvDTE.FileCodeModel> , доступны из <xref:EnvDTE.Project> объекта и выглядят следующим образом:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Можно выбрать реализацию только `CodeModel` `FileCodeModel` интерфейса или в объекте, возвращаемом из `Project` <xref:EnvDTE.ProjectItem> объектов и. Предоставьте все функциональные возможности этого интерфейса, которые подходят для вашей системы проектов.

 Если вы хотите добавить такие компоненты, как методы или свойства, которые недоступны из стандартных `CodeModel` `FileCodeModel` интерфейсов и, создайте собственный интерфейс, наследующий от стандартного. Не забудьте задокументировать его в системе проекта, чтобы конечные пользователи могли найти его. Вы возвращаете стандартный интерфейс, но пользователь может вызвать `QueryInterface` метод или выполнить приведение к интерфейсу, если известно, что он существует.

## <a name="see-also"></a>См. также раздел
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)
