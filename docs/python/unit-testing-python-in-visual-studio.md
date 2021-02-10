---
title: Модульное тестирование кода Python
description: Настройте модульное тестирование кода Python в Visual Studio и воспользуйтесь всеми преимуществами функций обнаружения, выполнения и отладки тестов в обозревателе тестов.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: aec13b3b35c75ecaad938cd3200f3af2a87d2441
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920655"
---
# <a name="set-up-unit-testing-for-python-code"></a>Настройка модульного тестирования для кода Python

Модульные тесты — это сегменты кода, которые проверяют работу других частей кода в приложении, например изолированных функций, классов и т. д. Если приложение успешно проходит все модульные тесты, то вы по меньшей мере уверены, что все низкоуровневые функции работают правильно.

В Python модульное тестирование широко используется для проверки скриптов в процессе разработки. Поддержка Python в Visual Studio включает обнаружение, выполнение и отладку модульных тестов непосредственно в контексте процесса разработки, а значит, вам не потребуется выполнять эти тесты отдельно.

Эта статья содержит краткий обзор модульного тестирования в Visual Studio для Python. Общие сведения о модульном тестировании см. в статье о [модульном тестировании кода](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end