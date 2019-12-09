---
title: Добавление проверки на NULL для всех параметров
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782345"
---
# <a name="add-null-checks-for-all-parameters"></a>Добавление проверки на null для всех параметров 

Область применения этого рефакторинга: 

- C# 

**Что?** Создает и добавляет инструкции `if`, которые проверяют наличие значения NULL для всех непроверенных параметров, допускающих это значение. 

**Когда?** Если нужно быстро добавить проверки на NULL для всех применимых параметров метода.

**Зачем?** Написание проверок на NULL для большого количества параметров может быть затратной по времени и утомительной задачей. Использование этого рефакторинга выполняется быстро и делает программу более надежной.  

## <a name="how-to"></a>Практические советы 

1. Поместите курсор в любой параметр в методе.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Быстрые действия и рефакторинг](media/add-null-checks-for-all-parameters.png)
   
3. Выберите параметр **Add null checks for all parameters** (Добавить проверки значений NULL для всех параметров).

   ![Добавление проверки на NULL для всех](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>См. также 

- [Рефакторинг](../refactoring-in-visual-studio.md)
