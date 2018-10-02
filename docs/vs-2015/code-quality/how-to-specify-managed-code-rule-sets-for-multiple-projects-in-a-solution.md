---
title: 'Практическое: определение набора правил управляемого кода для нескольких проектов в решении | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42b04eb88e6edee2d8250ac29a26f4cfe6562a29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563886"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Практическое руководство. Определение набора правил для управляемого кода в решении для нескольких проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: укажите управляемого кода наборов правил для нескольких проектов в решении](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution).  
  
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



