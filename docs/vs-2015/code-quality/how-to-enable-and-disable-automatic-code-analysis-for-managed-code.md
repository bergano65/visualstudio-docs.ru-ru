---
title: Практическое руководство. Включение и отключение автоматического анализа кода для управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c4f5de2926cb38f570defa95463489523c694132
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142290"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Практическое руководство. Включение и отключение автоматического анализа кода для управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить анализ кода для запуска перед каждым построением проекта управляемого кода. Можно задать разные свойства анализа кода для каждого [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] конфигурации.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>Включение или отключение автоматического анализа кода  
  
1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства**.  
  
2. В диалоговом окне свойств проекта щелкните **анализа кода**.  
  
3. Укажите тип сборки в **конфигурации** и целевую платформу в **платформы**.  
  
4. Чтобы включить или отключить анализ кода, установите или снимите **включить анализ кода в построении (определяет константу CODE_ANALYSIS)** "флажок".
