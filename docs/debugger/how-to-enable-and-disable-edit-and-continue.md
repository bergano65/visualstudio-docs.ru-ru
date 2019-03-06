---
title: 'Практическое: Включение и отключение изменить и продолжить | Документация Майкрософт'
ms.custom: seodec18
ms.date: 10/04/2018
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
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 49ee21943f63cee3fff35d2bb92817294169c61f
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223589"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Практическое: Включение и отключение изменить и продолжить (C#, VB, C++)

Можно включить или отключить **изменить и продолжить** в Visual Studio **параметры** диалоговое окно во время разработки. Операция **Изменить и продолжить** работает только в отладочных сборках. Дополнительные сведения см. в разделе [Изменить и продолжить](../debugger/edit-and-continue.md).

Для машинного кода C++ **изменить и продолжить** , необходимо использовать `/INCREMENTAL` параметр. Дополнительные сведения о требованиях к функции в C++ см. в этом [блога](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) и [изменить и продолжить (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

**Чтобы включить или отключить, изменить и продолжить:**

1.  Если вы в сеансе отладки, Остановите отладку (**Отладка** > **остановить отладку** или **Shift**+**F5**) .

1.  В **средства** > **параметры** > (или **Отладка** > **параметры**) > **отладки**  >  **Общие**выберите **изменить и продолжить** в области справа.

    > [!NOTE]
    >  Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в разделе [IntelliTrace](../debugger/intellitrace.md).

1.  Для кода C++, убедитесь, что **включить собственный изменить и продолжить** выбран и задать дополнительные параметры:
    - **Применить изменения при продолжении (только машинный код)**

      Если флажок установлен, Visual Studio автоматически компилирует и применяет изменения кода при продолжении отладки из состояния приостановки. В противном случае вы можете применить изменения с помощью **Отладка** > **применить изменения кода**.

    - **Предупреждать об устаревшем коде (только машинный код)**

      Если флажок установлен, выдавать предупреждения об устаревшем коде.

1.  Нажмите кнопку **ОК**.
