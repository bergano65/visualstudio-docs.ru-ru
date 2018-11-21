---
title: 'Практическое: отображение и скрытие групп регистров | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a98927d0132402e2977d5d8f1f28cbba43da636c
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257151"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Практическое: отображение и скрытие групп регистров (C#, C++, Visual Basic, F#)

**Регистрирует** окно доступно только в том случае, если включена отладка на уровне адреса в **параметры** диалоговом окне **Отладка** узел, **Общие**категории.  
  
 Чтобы избежать загромождения, **регистрирует** окно регистры организованы по группам. Если щелкнуть правой кнопкой мыши **регистрирует** окне появится контекстное меню, содержащее эти группы, которые можно отобразить или скрыть по своему усмотрению с помощью процедуры, описанной ниже.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-or-hide-register-groups"></a>Чтобы показать или скрыть группы регистров  
  
1.  Щелкните правой кнопкой мыши **регистрирует** окна.  
  
2.  Выберите в контекстном меню группы регистров, которые нужно показать или скрыть.  
  
     Группы регистров, не поддерживаемые оборудованием, на котором выполняется отладка, недоступны в контекстном меню, поэтому они не могут быть выбраны.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Использование окна регистров](../debugger/how-to-use-the-registers-window.md)