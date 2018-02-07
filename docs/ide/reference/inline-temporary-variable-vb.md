---
title: "Замена временной переменной ее значением в Visual Basic | Документация Майкрософт"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Замена временной переменной в Visual Basic

**Что?** Удаление временной переменной и ее замена значением.

**Когда?** Использование временной переменной затрудняет понимание кода.

**Зачем?** Удаление временной переменной может сделать код более удобным для чтения.

**Как?**

1. Выделите временную переменную или наведите на нее курсор для замены:

   ![Выделенный код](media/inline-highlight-vb.png)

1. Затем выполните одно из следующих действий:
   * **Клавиатура**
     * Нажмите клавиши **CTRL + .**, чтобы открыть меню **Быстрые действия и рефакторинг**.
   * **Мышь**
     * Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.

1. Выберите **Встроенная временная переменная** в контекстном меню окна предварительного просмотра.

   Переменная будет удалена и сразу же заменена значением переменной.

   ![Встроенный результат](media/inline-result-vb.png)

## <a name="see-also"></a>См. также

[Рефакторинг](../refactoring-in-visual-studio.md)