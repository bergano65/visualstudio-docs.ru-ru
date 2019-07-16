---
title: DA0029. Неподдерживаемая версия среды CLR | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152635"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029. Неподдерживаемая версия среды CLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ИД правила | DA0029 |  
| Категория | Использование средств профилирования |  
| Метод профилирования | Профилирование из командной строки |  
| Сообщение | Во время сбора обнаружена неподдерживаемая версия среды CLR. Управляемые символы могут разрешаться неправильно.|  
| Тип правила | Сведения. |  
  
## <a name="cause"></a>Причина  
 Предпринята попытка профилирования приложения, в котором используется платформа [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)], не поддерживаемая Средствами профилирования.  
  
## <a name="rule-description"></a>Описание правила  
 Это предупреждение выдается по той причине, что Средствам профилирования не удается разрешить символы в управляемом коде, выполняющемся в приложении. Средства профилирования не могут разрешать символы управляемого кода в приложениях для платформы [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Отсутствует.
