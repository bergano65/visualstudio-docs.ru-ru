---
title: "Как: определение набора правил для управляемого кода для нескольких проектов в решении | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1434e095fbf5c20286626cdc4cdc96716f2b9e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Практическое руководство. Определение набора правил для управляемого кода в решении для нескольких проектов
По умолчанию всех управляемых проектов решения назначаются Минимально рекомендованные правила анализа кода *набор правил*. Вы можете изменять наборы правил, назначенные проекту решения в диалоговом окне свойств решения.  
  
> [!NOTE]
>  По умолчанию проекта анализа кода не выполняется на этапе построения. Чтобы включить анализ кода в качестве шага построения, в разделе [как: Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Чтобы указать набор правил для нескольких проектов в решении с управляемым кодом  
  
1.  В [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]. [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] или [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] откроют решение.  
  
2.  На **анализ** меню, нажмите кнопку **Настройка анализа кода для решения**.  
  
3.  При необходимости разверните **общие свойства**, а затем нажмите кнопку **параметры анализа кода**.  
  
4.  Можно указать набор правил для одного или нескольких проектов.  
  
    -   Чтобы задать набор правил для отдельного проекта, щелкните имя проекта.  
  
    -   Чтобы указать набор правил для нескольких проектов, удерживая нажатой клавишу CTRL и щелкайте имена проектов.  
  
    -   Чтобы указать все проекты в решении, удерживая клавишу SHIFT, щелкните в списке проектов.  
  
5.  Нажмите кнопку **набор правил** поля проекта и выберите имя правила набора, что вы хотите применить.