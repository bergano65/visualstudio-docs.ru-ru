---
title: 'Как: Включение и отключение изменить и продолжить (C#, VB, C++) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9070913d1106eb5e2ca04160ad95c6a6fd46f752
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480457"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Как: Включение и отключение изменить и продолжить (C#, VB, C++)
Можно отключить или включить изменить и продолжить в **параметры** диалогового окна во время разработки. Этот параметр невозможно изменить в процессе отладки.  
  
Операция "Изменить и продолжить" работает только в отладочных сборках. В случае машинного кода C++ для операции "Изменить и продолжить" требуется использовать параметр /INCREMENTAL. Дополнительные сведения о требованиях к функции в C++ см. в этой [блога](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) и [изменить и продолжить (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Чтобы включить или отключить режим "Изменить и продолжить"  
  
1.  Если вы находитесь в сеанс отладки, остановить отладку (**Shift + F5**).

2.  Откройте страницу параметров отладки (**Сервис > Параметры > Отладка**).
  
3.  Выберите **Общие**и прокрутите вниз до **изменить и продолжить** категории (правая панель).  
  
4.  Чтобы включить, установите **включить изменить и продолжить** флажок. Чтобы отключить, снимите флажок.  
  
    > [!NOTE]
    >  Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в разделе [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Чтобы включить, установите **включить собственный изменить и продолжить**. Чтобы отключить, снимите флажок.

6. (C++) Задайте дополнительные параметры для машинного кода.

    - **Применить изменения при продолжении (только машинный код)**  
        Visual Studio автоматически компилирует и применяет необработанные изменения кода, внесенные при продолжении процесса из состояния приостановки. Если не выбран, можно применить изменения с помощью элемента «Применить изменения кода» в меню "Отладка".  
  
    - **Предупреждать об устаревшем коде (только машинный код)**  
        Получать предупреждения об устаревшем коде. 
  
7.  Нажмите кнопку **ОК**.    
  
## <a name="see-also"></a>См. также  
 [Изменить и продолжить](../debugger/edit-and-continue.md)