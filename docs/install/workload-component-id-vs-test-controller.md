---
title: Идентификаторы рабочих нагрузок и компонентов для Visual Studio Test Controller 2017
description: Идентификаторы рабочих нагрузок и компонентов Visual Studio можно использовать для распространения автоматических тестов на несколько компьютеров
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 08/14/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: fbbda9c8-d2c6-474d-b52d-a95227d52fe7
ms.workload:
- multiple
ms.openlocfilehash: 99225fc59211dd84af533e5c6825f429daf7ad3e
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139036"
---
# <a name="visual-studio-test-controller-2017-component-directory"></a>Каталог компонентов для Visual Studio Test Controller 2017

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки или в качестве зависимости в манифесте VSIX. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты.
* По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Когда вы включаете зависимости в манифест VSIX, достаточно указать только идентификаторы компонентов. Таблицы на этой странице позволяют определить минимальный набор зависимостей компонентов. В некоторых сценариях нужно указать лишь один компонент из рабочей нагрузки. В других случаях потребуется несколько компонентов из одной рабочей нагрузки или несколько компонентов из нескольких рабочих нагрузок. Дополнительные сведения см. в статье [How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) (Руководство по переносу проектов расширения среды на Visual Studio 2017).

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-controller"></a>Test Controller

**Идентификатор.** Microsoft.VisualStudio.Workload.TestController

**Описание.** Распределение автоматических тестов на несколько компьютеров.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestController | Основные функции Test Controller | 15.6.27309.0 | Обязательно

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Версия
--- | --- | ---
Н/Д | Н/Д | Н/Д

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>См. также

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
