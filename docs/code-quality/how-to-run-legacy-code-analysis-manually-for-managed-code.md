---
title: 'Как: Запуск устаревшего анализа кода вручную для управляемого кода'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432087"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Как: Запуск устаревшего анализа кода вручную для управляемого кода
Инструмент анализа кода предоставляет вам информацию о возможных дефектах в исходном коде. Вы можете автоматически запускать анализ кода с каждой сборкой кода проекта, а также можно запускать анализ кода вручную. Правила, проверяемые при запуске анализа кода, указаны на странице анализа кода страниц свойств проекта. Для получения дополнительной информации [см.](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)

## <a name="to-run-code-analysis-manually"></a>Для ручного выполнения анализа кода

1. Если вы находитесь на Visual Studio 2019 версии 16.5 или позже, выполните следующую команду по команде запрос перед запуском Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. В **Solution Explorer**щелкните проект.

3. В меню **«Анализ»** нажмите **«Анализ кода выполнить» по** *названию проекта.*

