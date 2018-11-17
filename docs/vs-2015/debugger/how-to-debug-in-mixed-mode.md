---
title: 'Практическое: отладка в смешанном режиме | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ee85e5822d4792046c755c85d699dd6a9a5d26
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737163"
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



