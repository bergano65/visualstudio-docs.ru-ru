---
title: Как запустить анализ кода прежних версий вручную для управляемого кода
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38c3de83dc0df39314ad236f647c69bbe614b75d
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371824"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Как выполнить анализ кода прежних версий вручную для управляемого кода
Средство анализа кода предоставляет сведения о возможных дефектах в исходном коде. Вы можете выполнять анализ кода автоматически при каждой сборке проекта кода, а также выполнять анализ кода вручную. Правила, проверяемые при выполнении анализа кода, указываются на странице "анализ кода" страниц свойств проекта. Дополнительные сведения см. [в разделе инструкции. Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Запуск анализа кода вручную

1. Если вы используете Visual Studio 2019 версии 16,5 или более поздней, перед запуском Visual Studio выполните в командной строке следующую команду:

```
set EnableLegacyCodeAnalysis = true
```

2. В **Обозреватель решений**щелкните проект.

3. В меню **анализ** выберите пункт **выполнить анализ кода для** *имени проекта*.

