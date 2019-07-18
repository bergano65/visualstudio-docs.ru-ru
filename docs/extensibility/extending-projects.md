---
title: Расширение проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0333e09aee207e10657999dda4b5b1d59e181cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341112"
---
# <a name="extend-projects"></a>Расширения проектов
Проекты и решения, способы, с помощью Visual Studio файлы кода и ресурсов организованы по единицы компиляции и развертывания. Можно найти дополнительные сведения о проектах в [проектов (Visual Studio SDK)](../extensibility/extending-projects.md).

 Можно создать собственные типы проектов с помощью Visual Studio SDK и Managed Package Framework для проектов, которые можно загрузить на [Managed Package Framework для проектов](https://github.com/tunnelvisionlabs/MPFProj10). Чтобы понять способ реализации пользовательских проектов, см. в разделе [Создание нового проекта: Это работает, часть один](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) и [Создание нового проекта: За кулисами, часть вторая](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 В этом разделе описываются способы создания пользовательских проектов и как управлять различными типами решение Visual Studio.

## <a name="in-this-section"></a>Содержание раздела
- [Создание системы базового проекта, часть 1](../extensibility/creating-a-basic-project-system-part-1.md) описывается создание системе пользовательских проектов.

- [Создание системы базового проекта, часть 2](../extensibility/creating-a-basic-project-system-part-2.md) описывается создание системе пользовательских проектов.

- [Сохранить данные в файлах проекта](../extensibility/saving-data-in-project-files.md) Explains, как добавить к проекту (<em>.</em> proj *) файлы.

- [Проверка подтипов проекта во время выполнения](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) объясняется, как проверить подтип проекта во время выполнения.

- [Добавление и удаление страниц свойств](../extensibility/adding-and-removing-property-pages.md) рассматривается настройка страницы свойств пользовательского проекта.

- [Добавить атрибут к элементу проекта](../extensibility/adding-an-attribute-to-a-project-item.md) объясняется, как добавить атрибут к элементу пользовательского проекта.

- [Сохранить свойство элемента проекта](../extensibility/persisting-the-property-of-a-project-item.md) объясняется, как сохранить свойства элемента пользовательского проекта.

- [Управление универсальных проектов Windows](../extensibility/managing-universal-windows-projects.md) содержатся сведения об управлении универсальных проектов.