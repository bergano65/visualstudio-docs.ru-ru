---
title: Обеспечение автоматизации кода Документы Майкрософт
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
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705994"
---
# <a name="providing-automation-for-code"></a>Предоставление автоматизации для кода
Создание модели автоматизации для кода не требуется. SDK окружающей среды не предоставляет выборку для этого. Чтобы понять модели кода, ознакомьтесь с объектом. <xref:EnvDTE.CodeModel>

 Для реализации модели кода необходимо реализовать любые интерфейсы, определяемые внутренней структурой данных. Объекты должны быть выведены из `IDispatch` класса.

 Объекты, которые <xref:EnvDTE.CodeModel> вы <xref:EnvDTE.FileCodeModel>расширяете, <xref:EnvDTE.Project> и, доступны от объекта, и выглядят следующим образом:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Вы можете выбрать для `CodeModel` реализации только или `FileCodeModel` интерфейс `Project` в <xref:EnvDTE.ProjectItem> объекте вы возвращаетеся из вашего и объектов. Предоставьте любую функциональность из этого интерфейса, который подходит для вашей проектной системы.

 Если вы хотите добавить функции, такие как методы или `CodeModel` `FileCodeModel` свойства, которые не доступны из стандарта и интерфейсов, создайте свой собственный интерфейс, который наследует от стандарта. Не забудьте задокументировать его с вашей системой проекта, чтобы конечные пользователи знали, чтобы искать его. Вы возвращаете стандартный интерфейс, но `QueryInterface` пользователь может вызвать метод или отлитый в интерфейс, если он, как известно, существует.

## <a name="see-also"></a>См. также
- [Общие сведения о модели автоматизации](../../extensibility/internals/automation-model-overview.md)
