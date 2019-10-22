---
title: Как задать наборы правил для управляемого кода для нескольких проектов в решении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656425"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Практическое руководство. Определение набора правил для управляемого кода в решении для нескольких проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию всем управляемым проектам решения назначается *набор правил*анализа кода "минимально рекомендованные правила Майкрософт". Вы можете изменить наборы правил, назначенные проектам решения, в диалоговом окне Свойства для решения.

> [!NOTE]
> По умолчанию анализ кода проекта не выполняется как шаг сборки. Сведения о включении анализа кода в качестве этапа построения см. [в разделе как настроить анализ кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Указание набора правил для нескольких проектов в решении с управляемым кодом

1. В [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] или [!INCLUDE[vsPro](../includes/vspro-md.md)] откроют решение.

2. В меню **анализ** выберите пункт **настроить анализ кода для решения**.

3. При необходимости разверните узел **Общие свойства**и выберите **Параметры анализа кода**.

4. Можно указать набор правил для одного или нескольких проектов.

    - Чтобы указать набор правил для отдельного проекта, щелкните имя проекта.

    - Чтобы указать набор правил для нескольких проектов, щелкните имена проектов, удерживая нажатой клавишу CTRL.

    - Чтобы указать все проекты в решении, удерживайте нажатой клавишу SHIFT и щелкните список проектов.

5. Щелкните поле **набора правил** проекта, а затем щелкните имя набора правил, который необходимо применить.
