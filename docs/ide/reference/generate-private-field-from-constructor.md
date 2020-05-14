---
title: Создание скрытого поля в конструкторе
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094018"
---
# <a name="generate-private-field-from-constructor"></a>Создание скрытого поля в конструкторе

Область применения этого рефакторинга: 

- C# 

- Visual Basic

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
