---
title: Включение и отключение автоматического анализа кода для управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d87cc57b31e63ae7aafa53c335df2b56f86a0409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658104"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Практическое руководство. Включение и отключение автоматического анализа управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить выполнение анализа кода перед каждой сборкой проекта управляемого кода. Для каждой конфигурации можно задать различные свойства анализа кода [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

### <a name="to-enable-or-disable-automatic-code-analysis"></a>Включение или отключение автоматического анализа кода

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и выберите пункт **Свойства**.

2. В диалоговом окне Свойства проекта щелкните **анализ кода**.

3. Укажите тип сборки в поле **Конфигурация** и Целевая платформа на **платформе**.

4. Чтобы включить или отключить автоматический анализ кода, установите или снимите флажок **Включить анализ кода для сборки (определяет CODE_ANALYSIS константу)** .
