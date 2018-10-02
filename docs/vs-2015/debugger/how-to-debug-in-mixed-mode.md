---
title: 'Практическое: отладка в смешанном режиме | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce056b60a3e080490a2ad60f4aee5a7b5c8dd63
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558691"
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: отладка в смешанном режиме](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-in-mixed-mode).  
  
Далее описывается отладка управляемого и машинного кода, также называемая отладкой в смешанном режиме. Для этого существует два скрипта, в зависимости от того, написана ли в машинном коде DLL-библиотека или приложение:  
  
-   Приложение, вызывающее DLL-библиотеку, написано в машинном коде. В этом случае DLL-библиотека является управляемой, и для отладки должны быть включены оба отладчика — управляемый и машинного кода. Это можно проверить в  **\<проект > страницы свойств** диалоговое окно. Способ выполнения этой операции зависит от того, откуда была запущена отладка: из проекта DLL или из проекта вызывающего приложения.  
  
-   Приложение, вызывающее DLL-библиотеку, написано в управляемом коде, а DLL-библиотека — в машинном.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Включение смешанного режима отладки  
  
1.  В **обозревателе решений**, выберите проект.  
  
2.  На **представление** меню, щелкните **страницы свойств**.  
  
3.  В  **\<проект > страницы свойств** диалогового окна разверните узел **свойства конфигурации** узел, а затем выберите **Отладка**.  
  
4.  Задайте **тип отладчика** для **смешанной** или **автоматически**.  
  
## <a name="see-also"></a>См. также  
 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)



