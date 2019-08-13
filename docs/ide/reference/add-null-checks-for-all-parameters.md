---
title: Добавление проверки на NULL для всех параметров
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712736"
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
