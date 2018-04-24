---
title: Практическое руководство. Включение и отключение автоматического анализа управляемого кода
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e47e2b760c65e64ee8c5fcad145a45c27e43adc8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Как: Включение и отключение автоматического анализа кода для управляемого кода

Можно настроить анализ кода для выполнения после каждой сборки проекта управляемого кода. Можно задать другой код свойства анализа для каждой конфигурации сборки.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Включение или отключение автоматического анализа кода

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите **свойства**.

1. В диалоговом окне свойств проекта выберите **анализа кода**.

1. Укажите тип сборки в **конфигурации** и целевую платформу в **платформы**.

1. Чтобы включить или отключить анализ кода, установите или снимите **включить анализ кода в построении** флажок.
