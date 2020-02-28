---
title: Создание скрытого поля в конструкторе
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529416"
---
# <a name="generate-private-field-from-constructor"></a>Создание скрытого поля в конструкторе

Область применения этого рефакторинга: 

- C# 

**Что?** Создание скрытого поля в конструкторе. 

**Когда?** Необходимо быстро добавить скрытое поле из конструктора.

**Зачем?** Запись скрытых полей может быть долгой и повторяющейся задачей. Использование этого рефакторинга выполняется быстро и делает программу более надежной.

## <a name="how-to"></a>Практические советы 

1. Поместите курсор на имя параметра в конструкторе.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
   
3. Выберите этот параметр, чтобы **создать и инициализировать поле**.

   ![Создание скрытого поля в конструкторе](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>См. также 

- [Рефакторинг](../refactoring-in-visual-studio.md)
