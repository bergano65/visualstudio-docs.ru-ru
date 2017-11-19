---
title: "Как: Включение и отключение автоматического анализа кода для управляемого кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad960a490d92e84efdfbd73e9aa23d7b41dc0dd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Практическое руководство. Включение и отключение автоматического анализа управляемого кода
Можно настроить выполнение перед каждой сборкой управляемого кода проекта анализа кода. Можно задать разные свойства анализа кода для каждого [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] конфигурации.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>Включение или отключение автоматического анализа кода  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и выберите команду **свойства**.  
  
2.  В диалоговом окне свойств проекта выберите **анализа кода**.  
  
3.  Укажите тип сборки в **конфигурации** и целевую платформу в **платформы**.  
  
4.  Чтобы включить или отключить анализ кода, установите или снимите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** флажок.