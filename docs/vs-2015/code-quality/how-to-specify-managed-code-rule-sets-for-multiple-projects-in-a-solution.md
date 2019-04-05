---
title: Практическое руководство. Определение набора правил управляемого кода для нескольких проектов в решении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2bf83c66f86d516d18221d01470e125979d39349
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979425"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Практическое руководство. Определение набора правил для управляемого кода для нескольких проектов в решении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию все управляемые проекты решения назначаются Microsoft минимальные рекомендуемые правила анализа кода *набор правил*. Вы можете изменить наборы правил, которые назначаются проектам решения в диалоговом окне "Свойства" для решения.  
  
> [!NOTE]
>  По умолчанию анализ кода проекта в качестве шага сборки не выполняется. Чтобы включить анализ кода в качестве шага сборки, см. в разделе [как: Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Чтобы указать набор правил для нескольких проектов в решении с управляемым кодом  
  
1.  В [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] или [!INCLUDE[vsPro](../includes/vspro-md.md)] откроют решение.  
  
2.  На **анализ** меню, щелкните **Настройка анализа кода для решения**.  
  
3.  При необходимости разверните **общие свойства**, а затем нажмите кнопку **параметры анализа кода**.  
  
4.  Можно указать набор правил для одного или нескольких проектов.  
  
    -   Чтобы указать набор правил для отдельного проекта, щелкните имя проекта.  
  
    -   Чтобы указать набор правил для нескольких проектов, удерживайте нажатой клавишу CTRL и щелкайте имена проектов.  
  
    -   Чтобы выбрать все проекты в решении, удерживая нажатой клавишу SHIFT и щелкните в списке проектов.  
  
5.  Нажмите кнопку **набора правил** поля проекта и выберите имя правила набора, что вы хотите применить.
