---
title: Как включить и отключить функцию "изменить и продолжить" | Документация Майкрософт
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
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430534"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Как включить и отключить функцию "изменить и продолжить"C#(, VB C++,)

Можно отключить или включить функцию **"изменить и продолжить** " в диалоговом окне " **Параметры** " Visual Studio во время разработки. Операция **Изменить и продолжить** работает только в отладочных сборках. Дополнительные сведения см. в разделе [Изменить и продолжить](../debugger/edit-and-continue.md).

Для native C++, режим **"изменить и продолжить** " требует использования параметра `/INCREMENTAL`. Дополнительные сведения о требованиях к функциям в см. в этой записи C++ [блога](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) и в разделе ["изменить и продолжить"C++()](../debugger/edit-and-continue-visual-cpp.md).

**Чтобы включить или отключить функцию "изменить и продолжить", выполните следующие действия.**

1. Если вы находитесь в сеансе отладки, отключите отладку (**отладка**  > **закончить отладку** или **SHIFT** +**F5**).

1. В **меню сервис**  > **Параметры** > (или**Параметры** **отладки**  > ) > **Отладка**  > **Общие**, выберите **изменить и продолжить** на правой панели.

    > [!NOTE]
    > Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в разделе [IntelliTrace](../debugger/intellitrace.md).

1. Для C++ кода убедитесь, что выбран параметр **включить собственное изменение и продолжить** , и задайте дополнительные параметры.
    - **Применить изменения при продолжении (только машинный код)**

      Если этот флажок установлен, Visual Studio автоматически компилирует и применяет изменения кода при продолжении отладки из состояния останова. В противном случае можно применить изменения с помощью **отладки**  > **Применить изменения кода**.

    - **Предупреждать об устаревшем коде (только машинный код)**

      Если этот флажок установлен, выдает предупреждения об устаревшем коде.

1. Нажмите кнопку **ОК**.
